# CoreWeave alternatives: only need one GPU? Want to start today without a sales call? Self-serve H100 and A100 rates compared, and where a $300 credit fits

CoreWeave prices an HGX H100 node at $49.24 an hour ($6.16 per GPU-hour) and an 8x A100 at $21.60 ($2.70 per GPU-hour), quoted before CPU, RAM and storage, provisioned in eight-GPU blocks, and arranged through sales rather than a console. If your job fits on one to four cards, that minimum is what you're working around. Self-serve providers rent single GPUs at published rates from $1.09 to $6.43 an hour depending on the card, and you can have one running today.

Vultr is the odd one in that group: a general-purpose cloud that also sells GPU instances, with clusters you provision yourself from the console or API. If you want the GPU and the rest of your stack (compute, bare metal, block storage, InfiniBand) on one hourly bill, it's worth pricing next to the GPU specialists.

> **Quick pick:** Thunder Compute for the cheapest fixed A100 rate ($1.09/GPU-hr, per-minute billing), RunPod for the widest GPU catalogue and per-second billing ($3.99/GPU-hr H100), Lambda for H100 PCIe at $3.29. If you'd rather not run three vendors for GPU, storage and networking, 👉 [check Vultr's H100 GPU instances and the current hourly rate](https://www.vultr.com/products/cloud-gpu/nvidia-h100?ref=9738262-9J) and compare it against the table below.

## What Vultr actually gives you, and what I won't quote

Vultr's GPU line is built for people who want to click deploy rather than open a ticket. Its own H100 page states that Vultr Clusters are provisioned through the Console or API with "no need for reservations or special requests," which is the exact opposite of the constraint that sent you looking for CoreWeave alternatives.

| Topic | What Vultr publishes |
| --- | --- |
| Ordering | GPU instances deploy from the console; clusters provisioned via Console or API, scheduled with Slurm or Kubernetes |
| Interconnect | HGX H100 clusters joined by NVIDIA InfiniBand |
| Footprint | 34 cloud data center locations across six continents |
| Compliance | ISO and SOC 2+ |
| Billing | Hourly, pay-as-you-go, ordered self-serve |
| New-account credit | $300 promotional credit code, plus $200, $250 and a deposit match |

I'm not printing a per-GPU figure for Vultr here. Vultr prices GPU instances per plan, with vCPU, RAM, storage and bandwidth bundled into the hourly number, so a "per-GPU" rate only means something once you've picked the plan. The per-GPU figures floating around in comparison posts don't agree with each other, and at least one traces back to a pre-paid contract "starting at" price rather than the self-serve on-demand rate. Price the plan you'll actually deploy: 👉 [open a Vultr GPU instance page and read the rate on the configuration you want](https://www.vultr.com/products/cloud-gpu/nvidia-h100?ref=9738262-9J).

### The $300 credit, with the fine print that matters

Vultr's coupons page lists **FLY300VULTR** for $300 of promotional credit, alongside a $200 code, a $250 code and a dollar-for-dollar deposit match capped at $100. Every one of them carries the same footnote: new customers only, credit applies to select products only, cannot be combined with other offers, restrictions and terms apply.

Two things follow. It's credit, not cash, so it offsets eligible usage on your account rather than landing in a balance you can withdraw. And "select products" is doing real work in that sentence, so confirm the plan you want is eligible before you build a budget around it. 👉 [Read the current terms on Vultr's coupon page before you sign up](https://www.vultr.com/coupons?ref=9738262-9J).

## Why teams leave CoreWeave

The minimum purchase is the reason, almost every time. CoreWeave's HGX H100 and HGX A100 instances are priced and provisioned in eight-GPU blocks. The main exception is a single-GPU GH200 at $6.50 an hour; CoreWeave also publishes a single-GPU inference price per configuration, and its pricing page notes that rate applies to customers on its inference platform. Everything else in the HGX range comes eight at a time, and access runs through sales.

Billing is itemized per component, so GPU, CPU, RAM and storage each land on their own line. That's fine for a known training run and annoying when you're costing out a two-week experiment.

Per GPU, the numbers aren't bad. Spot capacity runs roughly 40–60% of on-demand depending on the card, reserved capacity goes up to 60% off, and ingress, egress and transfer are free, as are the Kubernetes control plane and SUNK. A team training a large model on multi-node clusters with a negotiated contract is CoreWeave's customer. A solo developer who needs one H100 for a week is not.

## CoreWeave alternatives with verified single-GPU rates

On-demand rates read from each provider's own pricing page on September 17, 2026. They change without notice.

| Provider | Single GPU | H100 $/GPU-hr | A100 80GB $/GPU-hr | Billing |
| --- | --- | --- | --- | --- |
| Thunder Compute | Yes | $3.20 | $1.09 | Per minute |
| RunPod | Yes | $3.99 | $1.79 | Per second |
| Lambda | H100 PCIe only | $3.29 | $2.79 | Per hour |
| Vast.ai | Yes | $6.43 | $1.44 | Per second |
| Crusoe | Yes | $4.50 | $2.00 | Per minute |
| Nebius | Yes | $4.50 | Not offered | Per hour |
| Modal | Yes, serverless | $3.95 | $2.50 | Per second, scale to zero |
| CoreWeave | No (8-GPU HGX) | $6.16 | $2.70 | Hourly, per component |

- **Lambda's A100 figure is a node price.** The 80GB A100 sells in 8-GPU nodes at $2.79/GPU-hr; only the H100 PCIe is a genuine single-GPU order. Lambda's prices exclude tax.
- **Vast.ai is a marketplace.** Figures are medians across current US and Canada listings, including compute plus 100GB of storage; bandwidth is billed separately and moves with host, region and demand. Same card, different price, per host.
- **Nebius has moved on from A100.** Its current line leads with H200 and Blackwell. A September 19 check showed its H100 at $3.85 rather than $4.50, so confirm before you budget.
- **CoreWeave's per-GPU numbers are node prices divided by eight**, before CPU, RAM and storage.

## Three ways a GPU pricing page misleads you

**1. The headline rate that requires a three-year commitment.** Paperspace displays $2.24/hr for an H100. Its own footnote labels that a 3-year-commitment rate and states the on-demand price is $5.95/hr. The same page also contains a $3.09 figure whose wrapper is hidden and whose spec list reads A100, so it isn't a purchasable H100 rate at all. If you see a number that beats every competitor by 40%, scroll to the footnote before you plan around it.

**2. "Single GPU available" isn't "single GPU purchasable."** Lambda advertises single-GPU access and does sell one H100 PCIe at a time, but its $2.79 A100 80GB rate is an eight-card node divided by eight. A team budgeting $2.79/hr for one A100 is budgeting for eight.

**3. Every per-GPU rate covers a different bundle.** CoreWeave's $6.16 excludes CPU, RAM and storage. Vast.ai's $1.44 A100 median includes 100GB of storage but bills bandwidth separately. Vultr bundles vCPU, RAM, storage and a bandwidth allowance into the plan price. Put three "per-GPU-hour" numbers side by side and you're comparing three different products.

## Billing granularity costs more than the rate on short jobs

The billing unit is the smallest increment you're charged for. Modal, RunPod and Vast.ai bill per second. Thunder Compute and Crusoe bill per minute. Lambda and Nebius list per hour.

On a single long training run, none of that matters. On forty two-minute test jobs it decides the bill, which is why RunPod advertising no charge during provisioning is worth more than a few cents off the headline rate. Before you queue up a batch of short runs, ask each provider what the rounding rule is on a 90-second job.

## Pick by what you're actually running

**One card, learning or fine-tuning a small model.** Thunder Compute at $1.09/GPU-hr for an A100 80GB, billed per minute, is the cheapest fixed rate in this comparison. RunPod's $1.79 with per-second billing is the alternative if you want a bigger GPU catalogue (24 models, RTX A5000 through B300) and 31 regions.

**Bursty inference that should cost nothing when idle.** Modal at $3.95/GPU-hr H100 and $2.50 A100, per second with scale to zero; the Starter plan is $0/month plus compute, Team is $250/month plus compute. RunPod's serverless tier is the other option, with cold starts under 200ms on its FlashBoot path.

**Multi-node training that needs InfiniBand.** Voltage Park rents from one GPU to 1,016-GPU clusters with up to 3200 Gbps InfiniBand, priced by quote. RunPod Clusters handles multi-node training self-serve with no contract. Vultr Clusters does the same through its Console or API with Slurm or Kubernetes scheduling, and no reservation step.

**You're already inside a hyperscaler.** AWS's 8x H100 p5.48xlarge works out to roughly $5.19 per GPU-hour at list (checked September 19, 2026), and Azure's H100 series starts around $6.98. You're paying for the network, IAM and data gravity you already have, not for the GPU.

## What switching actually costs

Containerized workloads move easily. Export your manifests, change the registry reference if the new provider needs it, and deploy on anyone who accepts standard Docker images. That covers most inference and fine-tuning work.

Egress is the line item people forget. CoreWeave, RunPod, Voltage Park, TensorDock and CloudRift all state no ingress or egress fees. Vast.ai bills bandwidth separately, so a cheap card on a host with expensive transfer can cost more than a mid-priced card on a host without it.

Storage and dataset reload time are the other two. Pulling a 500GB dataset onto a new provider takes hours you didn't budget, and persistent volumes are priced separately from the GPU on most of these platforms. If your data is already sitting in one cloud's object storage, that's a real argument for staying.

## FAQ

**Can you rent a single GPU from CoreWeave?** In one case: the GH200 at $6.50/hr. CoreWeave also publishes a single-GPU inference price for each configuration, restricted to inference platform customers. Every HGX configuration is eight cards, and access still runs through sales.

**Is CoreWeave expensive?** Per GPU, no. $6.16/hr for an H100 and $2.70 for an A100 sit mid-pack against specialists charging $3.20–$3.95 for an H100. With spot at 40–60% of on-demand, reserved discounts to 60%, and free transfer, the rates are competitive. The cost is the eight-card unit.

**Who doesn't charge for egress?** CoreWeave, RunPod, Voltage Park, TensorDock and CloudRift all state no ingress or egress fees. Everyone else needs checking, and marketplaces usually bill bandwidth separately.

**Will the $300 Vultr credit cover a GPU instance?** Vultr's coupon terms say promotional credit applies to select products only and can't be combined with other offers. Check that the plan you want is eligible before you count it.

## The decision, in one pass

Only need one or two cards and want to run this afternoon: Thunder Compute or RunPod. Bursty workloads where idle time should cost zero: Modal. Multi-node with InfiniBand and no reservation process: Vultr Clusters or RunPod Clusters. GPU plus compute, bare metal and storage on one hourly account: Vultr.

Before you enter a card anywhere, confirm two numbers: the on-demand rate for the exact plan you'll deploy (not the "starting at" or commitment figure), and the billing increment plus whether storage and bandwidth sit outside the GPU rate.

If the second number is what's been burning you, a general-purpose cloud is the simpler answer, and the $300 credit covers part of finding out: 👉 [start a Vultr account and price the GPU plan you'd actually run](https://bit.ly/VuLtr).
