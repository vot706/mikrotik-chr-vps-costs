# VPS MikroTik: Do you need to buy a CHR license, how cheap can a usable router be, and does annual billing pay off? (JustHost plan table, year-one vs year-two cost)

JustHost's cheapest VPS is **$1.99/month**, but that plan runs on a 10 Mbps fair-share port and the free CHR license caps RouterOS at 1 Mbit/s. The realistic floor for a router you would actually put in front of something is **$8.09/month** (1 GB RAM, 300 Mbps port), plus a **one-time $45 P1 license** from MikroTik.

The rest of this page covers three things that most MikroTik VPS pages skip: which license tier JustHost's port speeds actually justify, what the first year and second year really cost once the license is in the math, and which plan size fits which workload. Prices below are the ones JustHost lists on its international VPS page.

> **Quick pick:** Sirius at **$8.09/month** ($6.47/month equivalent on a 12-month term) plus a $45 P1 key. It is $1.73 more than the 1 GB entry plan and gives you three times the port speed and twice the disk. Skip the license tiers above P1 on this host entirely.
> 👉 [Check JustHost's current VPS plans and prices](https://justhost.asia/?ref=196392)

## What JustHost actually sells

JustHost runs KVM VPS with NVMe storage, a fair-share unmetered port, built-in DDoS filtering, and the ability to add CPU, RAM or disk later without migrating to another server. MikroTik RouterOS is one of the images offered alongside Ubuntu, Debian and the usual panel options, which is what makes these plans relevant to a `vps mikrotik` search in the first place.

Two things to know before the table:

- **The port speed is the real specification.** Traffic is unmetered on a fair-share basis, so you will not get a bandwidth bill. You will also not get a guaranteed rate at peak hours. The "equivalent to 93+ TB/month" figures are what the port could theoretically move if it ran flat out for a month.
- **The 20% annual discount requires a 3-month-or-longer order.** The left-hand price is month-to-month; the right-hand price is the effective monthly rate when you pay for 12 months.

| Plan | vCPU / RAM | NVMe | Port (fair-share) | Price (monthly → 12-mo) | Order |
| --- | --- | --- | --- | --- | --- |
| VPS Promo | 1 core / 512 MB | 5 GB | 10 Mbps | $1.99 → not published | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |
| New Star | 1 core / 1 GB | 10 GB | 100 Mbps | $6.36 → $5.09 | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |
| Sirius | 1 core / 1 GB | 20 GB | 300 Mbps | $8.09 → $6.47 | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |
| Double Star | 2 cores / 2 GB | 20 GB | 200 Mbps | $11.81 → $9.45 | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |
| Arcturus | 1 core / 2 GB | 30 GB | 300 Mbps | $11.54 → $9.23 | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |
| Alpha Centauri | 2 cores / 2 GB | 40 GB | 400 Mbps | $14.99 → $11.99 | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |
| Bright Star | 4 cores / 4 GB | 30 GB | 300 Mbps | $16.33 → $13.06 | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |
| Vega | 2 cores / 4 GB | 80 GB | 500 Mbps | $22.40 → $17.92 | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |
| Capella | 4 cores / 4 GB | 120 GB | 750 Mbps | $30.51 → $24.41 | [Open JustHost's plan list](https://justhost.asia/?ref=196392) |

The lineup continues above Capella with an 8 GB / 4-core / 200 GB configuration on the same 750 Mbps port; that price is on the order page rather than in the summary above.

The pattern worth noticing: moving up one tier usually buys you port speed and disk before it buys you RAM. Sirius versus New Star is the clearest case. Same core count, same 1 GB, double the disk, triple the port, $1.73 apart. Alpha Centauri versus Double Star repeats it at $3.18 apart. For a router, port speed is the resource you run out of first, so those upgrades are usually worth the small delta.

## The CHR license is a second purchase, and JustHost's ports decide which tier you need

CHR is RouterOS compiled to run as a virtual machine. It has the same feature set as a physical RouterBOARD minus the hardware-specific drivers: stateful firewall, NAT, VLANs and bridges, queue trees, Hotspot, PPPoE, IPsec, WireGuard, L2TP, SSTP, plus BGP, OSPF and MPLS in software. You manage it through WinBox, WebFig, SSH, the API or the terminal, which is why engineers who already know RouterOS can migrate a config in an evening rather than relearning a platform.

The license is separate from the VPS and bought once from MikroTik:

| License | Throughput cap | One-time cost |
| --- | --- | --- |
| Free | 1 Mbit/s per interface | $0 |
| P1 | 1 Gbps | $45 |
| P10 | 10 Gbps | $95 |
| P-Unlimited | Uncapped | $250 |

New CHR installs start on a 60-day trial at full speed, then drop to whatever license you have applied. Nothing renews, and nothing is charged per month.

Here is the part that matters for JustHost specifically. Every plan in that table tops out between 10 Mbps and 750 Mbps. The cheapest paid license, P1 at $45, already allows 1 Gbps, which is more than the fastest port JustHost sells. **On this host, P10 and P-Unlimited buy you nothing.** You would be paying $95 or $250 for a limit the hypervisor will hit first.

The reverse is also true and catches people out: a 300 Mbps port means nothing if your license is still on the free tier, because RouterOS will shape you to 1 Mbit/s regardless of what the network could carry. The two numbers are independent, and the effective ceiling is whichever is lower.

So the budget line is fixed: one $45 key, applied once, and it covers any JustHost plan you will ever upgrade to.

👉 [Start with a JustHost plan and apply your own P1 key](https://justhost.asia/?ref=196392)

## What the first two years actually cost

The license changes the shape of year one and then disappears from the math. Here is Sirius and Double Star, both with the $45 P1 key included:

| Plan | Year 1, monthly billing | Year 1, 12-month billing | Year 2, 12-month billing |
| --- | --- | --- | --- |
| Sirius | $142.08 | $122.64 | $77.64 |
| Double Star | $186.72 | $158.40 | $113.40 |

Annual billing saves $19.44 a year on Sirius and $28.32 on Double Star. On a $8.09 plan that is roughly two and a half months free, which is a normal annual discount, not a trap. JustHost's listed annual rates are the discounted rates rather than an introductory price that jumps at renewal, so year two costs the same as year one minus nothing.

What does move is the license. It is 37% of Sirius's year-one cost on monthly billing and 0% of year two. If you are only testing whether cloud RouterOS fits your network, that argues for paying monthly for two or three months, keeping the 60-day CHR trial running, and only then committing to 12 months once you know the config works.

For reference on how other hosts structure this: Cloudblast bills hourly as well as monthly from €3.60 and puts every plan on a 10 Gbps port with 5 TB of traffic; Cloudzy sells 1 GB at $3.48/month on a promotional 50% discount off $6.95, brings your own license, and offers 14-day refunds across 13 regions with 40 Gbps capable hardware; Perlod charges $8.99/month for 1 GB on a 1 Gbps port with 3 TB of traffic and gives 12% off annual. Those hosts give you enough port speed that a P10 key would have something to do. JustHost's cheaper ports are why the $45 key is the end of the line here.

👉 [Compare JustHost's monthly and 12-month pricing](https://justhost.asia/?ref=196392)

## Which plan for which job

**Lab work, a single WireGuard tunnel, a home router in the cloud.** VPS Promo at $1.99 is tempting and genuinely fine for a CHR you reboot weekly, but 10 Mbps and 512 MB gets tight the moment you add a second tunnel or a queue tree. Sirius at $8.09 is the smallest plan I would leave running. Free license is enough here if you only need a handful of Mbit/s; anything resembling production wants the $45 key.

**Branch site-to-site, a few dozen firewall rules, a VPN hub for remote staff.** Double Star or Alpha Centauri. Two vCPUs matter once you are doing IPsec or WireGuard encryption alongside NAT, and 200–400 Mbps of port is more than a typical branch uplink. 2 GB of RAM holds a full address-list and a moderate rule set without swapping.

**Hotspot or PPPoE for a small venue, per-subscriber queues.** Vega at $22.40, mostly for the 80 GB disk if you are keeping logs and accounting locally, and for the 500 Mbps port. Queue trees with PCQ on many clients are CPU-hungry; two cores is the minimum I would plan for.

**Anything that needs more than 750 Mbps of real forwarding, or a full BGP table with several upstreams at line rate.** JustHost is the wrong host. Its fastest port is 750 Mbps fair-share, which is below the P1 ceiling already. That workload belongs on a provider selling 10 Gbps ports, and it is the one case where paying for P10 makes sense.

## Where JustHost stops working

**Fair-share means no guaranteed rate.** Unmetered traffic is a genuine convenience, but during peak hours on a contended host your 300 Mbps port is a ceiling, not a promise. If you need committed bandwidth, this is not the product.

**The RouterOS image is worth checking before you pay.** The version in the panel decides whether you get 7.x with WireGuard support or an older branch with a legacy config path. Confirm which one is provisioned for the plan and location you pick, especially if you are migrating an existing `/export`.

**CHR has no hardware offload.** Bridging and heavy firewall work run on the vCPU. That is why the jump from one core to two matters more on RouterOS than on a general-purpose Linux VPS.

**Migrating from a physical box means rebinding interfaces.** A `/export` from a RouterBOARD pastes into CHR almost cleanly, but the interface names change to ether1, ether2 and so on. Expect to fix interface lists, bridge ports and anything referencing a physical port name. Typical configs take well under an hour.

**It is unmanaged.** You get root and a console. Nobody is going to debug your firewall rules for you, and that is true of nearly every host in this bracket.

**Confirm the refund terms yourself.** JustHost's public pages describe instant access after payment and 24/7 support, but do not state a money-back window for VPS plans the way Cloudzy (14 days) or Perlod (7 days) do. Ask support before you commit to 12 months.

👉 [See JustHost's VPS lineup before you order](https://justhost.asia/?ref=196392)

## FAQ

**Can I use a CHR license I already own?**
Yes. CHR keys are issued through your MikroTik account and applied inside RouterOS on the instance you designate. You are not dependent on the host to supply or activate anything.

**Can I run BGP on it?**
RouterOS supports BGP, OSPF and MPLS in software, so the routing side works. Whether any host will open a BGP session with you is a separate question, and the safe pattern is to build GRE or IPsec tunnels to your own upstreams and announce your prefixes over those rather than expecting the VPS provider to peer with you.

**Does RouterOS 6.x work?**
CHR 6.x exists, but 7.x is the realistic choice unless you are carrying a legacy config forward. Check the image version offered in the panel before ordering.

**How fast is delivery?**
JustHost provisions after payment clears and gives you control panel access at that point. It is not a manual setup queue.

**Can I upgrade later without reinstalling?**
Yes. CPU, RAM and disk can be increased on the existing server, so starting on Sirius and moving to Double Star or Vega later does not mean rebuilding the router.

**What is the 60-day trial?**
MikroTik ships new CHR installs with a 60-day full-speed trial before the license tier takes effect. It is long enough to build a config, run traffic through it and decide, which pairs well with a monthly billing cycle for the first couple of months.

## Final call

Match the plan to the port, not the RAM. If you need a lab router or a single tunnel, take **Sirius at $8.09** and run the free license until you actually push traffic. If you are putting CHR in front of a branch or a small client base, take **Double Star at $11.81** or **Alpha Centauri at $14.99** and budget the **$45 P1 key** once. If your requirement starts above 750 Mbps, stop here and look at hosts selling 10 Gbps ports, because no amount of license tier will get you past JustHost's uplink.

Two things to settle before you pay: which RouterOS version the image gives you, and what the refund terms are if you choose annual billing. Everything else on this host is priced clearly enough to decide from the table.

👉 [Open JustHost's plan list and pick the port speed you need](https://justhost.asia/?ref=196392)
