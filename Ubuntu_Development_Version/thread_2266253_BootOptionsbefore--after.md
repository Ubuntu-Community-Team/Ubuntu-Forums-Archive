---
title: "BootOptions/before--after"
date: 2015-02-21
forum: Ubuntu Development Version
---

### Post by sudodus on 2015-02-21
The "**-- **" entry defines the boundary  between options which are specific to the installer and ones that are  copied to the target system. Often you would like to copy the boot  option to the target system, so add the option at the very end of the  line, after the "**-- **".

This link [https://help.ubuntu.com/community/BootOptions/before--after](https://help.ubuntu.com/community/BootOptions/before--after)

describes a new way to use a boot option that is due to the introduction of systemd into Ubuntu. Sometimes it must be entered ***twice***, before and after the delimiter "**--**". 

```
... option -- option
```
[HR][/HR]Edit: ***I have found it in the new released version Ubuntu Server 14.04.2 LTS***
[HR][/HR]Originally I found it when testing future versions, but we expect it to come into at least the Ubuntu **mini.iso** file with the version 15.04.

[LIST]
[*]Ubuntu Vivid mini.iso (which will be released in April) 
[*]Lubuntu Trusty 14.04.2 alternate iso (which was not released due to show-stopping bugs) 
[/LIST]

I think it might also be present in the ***Ubuntu Server*** Vivid iso files. Do ***you*** know? Would you be interested to know? If you use boot options to install Ubuntu Server, it might be interesting to test it.

---

### Post by sudodus on 2015-02-21
I was too curious. I just had to grab **ubuntu-14.04.2-server-i386.iso **and test it.

This new point release of Ubuntu Server needs

```
... forcepae -- forcepae
```

to be able to install a minimal system or a server into my Thinkpad T41 with a Pentium M processor. So if you intend to use a boot option with Ubuntu Server 14.04.2, and if you need the boot option both during the installation and in the installed system, it should be entered twice.

---

