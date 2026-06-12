---
title: "Mitigating Spectre v2 issues"
date: 2023-01-22
forum: Security
---

### Post by wjmacfarland on 2023-01-22
I had a discussion with AI about the RETBleed security risk:

[TABLE="width: 500"]
[TR]
[TD]How can issues with Spectre v2 be mitigated for an Ubuntu VM?

Spectre v2 can be mitigated for an Ubuntu VM by disabling the “speculative store bypass” feature in the BIOS. Additionally, the “kernel page table isolation” feature can be enabled to help protect against this vulnerability. Lastly, regularly updating the system and applying the latest security updates will also help to reduce the risk of Spectre v2.

How can I set these things from the terminal of Ubuntu?

To set the “speculative store bypass” and “kernel page table isolation” features from the terminal of Ubuntu, you will need to use the command line. To disable the “speculative store bypass” feature, use the command “sudo x86_feature --disable ssbd”. To enable the “kernel page table isolation” feature, use the command “sudo x86_feature --enable kpti”.

What if the x86_feature command isn't found?

If the x86_feature command is not found, you may need to install it. To do so, use the command “sudo apt-get install x86_feature”. Once installed, you can then use the command to enable and disable the “speculative store bypass” and “kernel page table isolation” features.
[/TD]
[/TR]
[/TABLE]

However, Ubuntu 22.0.4 does not have x86_feature in the release list.
This means it's not easy to protect the machine from this type of attack, as far as I can tell.

Is there anything being done to secure Ubuntu machines?

---

### Post by alexmurray on 2023-01-22
A quick google for "retbleed ubuntu" would have taken you to [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/Retbleed](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/Retbleed) as the first hit - as can be seen the mitigations for the various retbleed CVEs have already been released via updated kernel packages, so there is nothing you should need to do to manually get these.

Don't trust AIs ;)

---

### Post by wjmacfarland on 2023-01-23
I guess I'll hold off until the public cloud images are available. Thanks for the information!

---

### Post by alexmurray on 2023-01-23
Public cloud images have been available for a while now - that page is just out of date.

---

