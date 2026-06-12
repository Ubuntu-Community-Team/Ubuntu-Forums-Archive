---
title: "Unable to modify XML file - need to add a serial port"
date: 2010-03-06
forum: Virtualisation
---

### Post by dc-spyder on 2010-03-06
I am running Ubuntu 9.10 Server and am using the KVM virtualization tool to run a couple of Windows XP SP2 guests.  On one of them I need to pass through the hardware serial port to the Windows XP client to interface with a solar electricity system.

I've tried to edit the /etc/libvirt/qemu/win_xp.xml file to include these directives:

<serial type='dev'>
 <source path='/dev/ttyS)'/>
 <target part='1'/>
</serial>

I save the file and then use virsh to update the guest:

virsh define win_xp.xml

But when I look at the xml file after the machine has started, I see the following where I should see my directives above:

   <serial type='dev'>
      <source path='/dev/ttyS0'/>
      <target port='0'/>
    </serial>
    <console type='dev'>
      <source path='/dev/ttyS0'/>
      <target port='0'/>
    </console>

As this maps to target port 0 (I assume this equates to COM0 in the Windows world), I cannot access that port in the Windows software (only accepts COM1-COM16).

So this is a two part question.  First, is my syntax correct above to add (what I assume is ttyS0 - the only physical DB9 serial port on the machine) the serial port as COM1 into the Windows XP guest?  Second, why does my configuration keep getting obliterated and replaced with some sort of "standard" template whenever I start the virtual machine?

---

### Post by dc-spyder on 2010-03-13
Can anybody give me a hint where to start looking for the answer to this issue?
 
Thanks.

---

