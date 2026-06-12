---
title: "Color of I-Beam when using RDP or in VirtualBox"
date: 2009-08-14
forum: Virtualisation
---

### Post by samalex on 2009-08-14
Hi,

Being a DBA who lives in MS SQL at work, I remote into my work desktop almost daily from home.  I've noticed that on my new System76 laptop whether I remote in through Windows XP (installed through VirtualBox 3) or through the Linux Terminal Services client the I-Beam cursor is always black.  This is the cursor that appears when you're over a text insertion point.

Due to a visual impairment I have my SQL editor set to have a black background with green text, so with the I-Beam being Black it disappears when hovering over the text window.  Remoting into the system through RDP on OSX or on another Windows box doesn't do this, the I-Beam turns white when on a black area, but through Linux in any case it remains black.

Does anyone know of some setting or something I can change so the I-Beam color will change?  Sorry, this might seem petty, but I'm finding it's a major problem when trying to work from home.  I can modify the black background, but being anything other than black makes it harder for me to read.

Thanks for any suggestions or help.  Also I'm using Gnome and Ubuntu 9.04 with all updates.

Sam

---

### Post by jocampo on 2009-08-14
> **samalex said:**
> Hi,

Being a DBA who lives in MS SQL at work, I remote into my work desktop almost daily from home.  I've noticed that on my new System76 laptop whether I remote in through Windows XP (installed through VirtualBox 3) or through the Linux Terminal Services client the I-Beam cursor is always black.  This is the cursor that appears when you're over a text insertion point.

Due to a visual impairment I have my SQL editor set to have a black background with green text, so with the I-Beam being Black it disappears when hovering over the text window.  Remoting into the system through RDP on OSX or on another Windows box doesn't do this, the I-Beam turns white when on a black area, but through Linux in any case it remains black.

Does anyone know of some setting or something I can change so the I-Beam color will change?  Sorry, this might seem petty, but I'm finding it's a major problem when trying to work from home.  I can modify the black background, but being anything other than black makes it harder for me to read.

Thanks for any suggestions or help.  Also I'm using Gnome and Ubuntu 9.04 with all updates.

Sam

Wish I can work/run my SQL console from Ubuntu too ;-) ...MS-SQL dba here also..

Check the menu options for the virtual-machine, you should have an option for the Mouse or Cursor, don't remember well ...

---

### Post by finn_h on 2010-10-25
There's a known bug in VirtualBox that causes this same problem for Windows XP VMs.

I just posted a workaround for the issue here on the bug itself:

[http://www.virtualbox.org/ticket/750#comment:17](http://www.virtualbox.org/ticket/750#comment:17)

Perhaps the same workaround (choosing a specific cursor that has both black & white in it, rather than one that inverts based on background) could be applied to your Ubuntu instance?

---

