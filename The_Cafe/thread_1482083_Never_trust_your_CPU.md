---
title: "Never trust your CPU"
date: 2010-05-13
forum: The Cafe
---

### Post by mmix on 2010-05-13
CPU watching you..
[http://www.theregister.co.uk/2010/05/12/tamper_evident_microprocessor/](http://www.theregister.co.uk/2010/05/12/tamper_evident_microprocessor/)

> 
Scientists have devised a chip design to ensure microprocessors haven't been surreptitiously equipped with malicious backdoors that could be used to siphon sensitive information or receive instructions from adversaries.

The on-chip engines at the heart of these "tamper evident microprocessors" are the computer equivalent of cellophane shrink wrap or aluminum seals that flag food or drug packages that have been opened by someone other than the consumer. They're designed to monitor operations flowing through a CPU for signs its microcode has been altered by malicious insiders during the design cycle.

The design, made public this week at the 31st IEEE Symposium on Security & Privacy, comes as an investigation by Engineering & Technology magazine reported that at least five percent of the global electronics supply chain includes counterfeit elements that could "cause critical failure or can put an individual's data at risk," according to The Inquirer. While most of that appears to be coming from grey-market profiteers, analysts have long fretted that bogus routers and microprocessors could pose a threat to national security.

"The root of trust in all software systems rests on microprocessors because all software is executed by a microprocessor," the scientists, from Columbia University's computer science department, wrote in their paper describing the design. "If the microprocessor cannot be trusted, no security guarantees can be provided by the system."

At the heart of their proposal are two engines hardwired into a processor that continuously monitor chip communications for anomalies. One of the engines, dubbed TrustNet, sends an alert whenever a unit executes more or fewer instructions than is expected. A second, called DataWatch, watches chip data for signs the CPU has been maliciously modified.

The engines are built to detect a variety of potential threats such as emitter backdoors, which typically append instructions to a processor's normal batch of communications so that data is copied to "shadow addresses" that can later be accessed by the attackers. They're also built to flag corrupter backdoors that subtly alter microarchitectural operations.

The defenses are premised on the assumption that the backdoors would be installed by insiders working in a single sub-unit of a design team. While a well-funded nation state could afford to buy out an entire team, the more likely scenario is that adversaries would be much more limited, the researchers said. The insiders would add the hidden instructions during the RTL, or register transfer level, phase of design, which involves writing the microcode that controls a chip's functions.

The scientists demonstrated the design on a simplified OpenSPARC T2 processor from Sun Microsystems and got promising results. All emitter and control corrupter attacks were flagged in all cases, and no false positives occurred. They also said the added performance costs were negligible, with less than 3 KB of storage required per processor core.

The scientists are Adam Waksman and Simha Sethumadhavan. A PDF of their paper is here. ®

---

### Post by NMFTM on 2010-05-13
So, wouldn't all the CPU's sold need to be tainted in order for it to work? I mean, if a government agency was going to buy a bunch of CPU's to use in upgrading their organization's computers they'd just order them from either AMD or Intel and they'd get sent a batch from the closest nearest warehouse.

So, assuming the CPU design team implimented those features in every single CPU. Wouldn't the people who wanted to use the CPU to break into computer systems have to know which CPU's the government agency was going? Which would require going through the logs of who bought the CPU's and getting the serial numbers of every CPU purchased by X government agency.

And even then, couldn't the government agnecy if they were that concerned about security order the CPU's under a fake business name? So the order would be to "Joe's Computer Repair" at 123 Whatever Street instead of to the order of the NSA at whatever the NSA HQ's address is.

---

