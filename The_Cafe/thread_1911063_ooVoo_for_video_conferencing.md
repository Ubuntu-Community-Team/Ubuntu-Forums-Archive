---
title: "ooVoo for video conferencing"
date: 2012-01-18
forum: The Cafe
---

### Post by briancb on 2012-01-18
Recently my company, which is international, has started using ooVoo for video conferencing. This means I have to stop using Ubuntu as my main OS.

---

### Post by haqking on 2012-01-18
> **briancb said:**
> Recently my company, which is international, has started using ooVoo for video conferencing. This means I have to stop using Ubuntu as my main OS.

Use wine or a virtual machine.

---

### Post by briancb on 2012-01-18
Thank you. Tried both no success.

---

### Post by haqking on 2012-01-18
> **briancb said:**
> Thank you. Tried both no success.

why not ?

if its in a virtual machine it is no different to a real HDD install.

There are tons of links on line about people using it in a VM.

Installing it in a virtual machine is no different to installing it elsewhere

---

### Post by wolfen69 on 2012-01-18
Just dual boot. Solved.

---

### Post by TheNerdAL on 2012-01-18
> **wolfen69 said:**
> Just dual boot. Solved.

This. 

Question: Is there a way to Dualboot with Ubuntu first? Or do you have to have Windows first all the time?

---

### Post by Grenage on 2012-01-18
> **TheNerdAL said:**
> This. 

Question: Is there a way to Dualboot with Ubuntu first? Or do you have to have Windows first all the time?

You can do it either way, it's just easier to install Windows first.  Grub needs to be reinstalled if it has been overwritten.

---

### Post by TheNerdAL on 2012-01-18
> **Grenage said:**
> You can do it either way, it's just easier to install Windows first.  Grub needs to be reinstalled if it has been overwritten.

Please link me to a site that tells me how. I want to dualboot, but don't want to install Windows first, then reinstall Ubuntu.

---

### Post by Grenage on 2012-01-18
> **TheNerdAL said:**
> Please link me to a site that tells me how. I want to dualboot, but don't want to install Windows first, then reinstall Ubuntu.

Have a look here:

[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

---

### Post by briancb on 2012-01-18
I have difficulty with connection also webcam & Mike.

---

### Post by briancb on 2012-01-18
That is what I do however the problem is I need to have ooVoo connected all the time, I do not know when somebody wants to contact me. Also there is the problem of emails as you cannot keep a record of all emails using both systems. If you send an email on one it is not available on the other.

---

### Post by haqking on 2012-01-19
> **briancb said:**
> That is what I do however the problem is I need to have ooVoo connected all the time, I do not know when somebody wants to contact me. Also there is the problem of emails as you cannot keep a record of all emails using both systems. If you send an email on one it is not available on the other.

ok well so you know oovoo can run in a virtual machine.

it seems more of a inexperience issue or troubleshooting issue for you personally, you dont have to remove ubuntu there are ways around it.

post your mic and cam issues and you may get help on how to fix them, if they work in windows or whatever on a HDD install there is no reason for them not to work in virtual machine.

Also as for emails, if you use IMAP then any email changes in one place will be reflected elsewhere, but that depends on your mail setup of course.

Cheers

---

### Post by briancb on 2012-01-19
> **haqking said:**
> ok well so you know oovoo can run in a virtual machine.

it seems more of a inexperience issue or troubleshooting issue for you personally, you dont have to remove ubuntu there are ways around it.

post your mic and cam issues and you may get help on how to fix them, if they work in windows or whatever on a HDD install there is no reason for them not to work in virtual machine.

Also as for emails, if you use IMAP then any email changes in one place will be reflected elsewhere, but that depends on your mail setup of course.

Cheers
Thank you for your answers. I will try a virtual machine again and try to persist to get things working. I may have given up too soon. If I get ooVoo working then the email question doesn't matter.

---

### Post by briancb on 2012-01-19
> **briancb said:**
> Thank you for your answers. I will try a virtual machine again and try to persist to get things working. I may have given up too soon. If I get ooVoo working then the email question doesn't matter.
Ok, sorted one problem you cannot use the Logitec Cam alongside a wireless mouse and keyboard. Used a standard mouse etc. and webcam works perfect. Now I have to sort out the distorted sound.

---

### Post by haqking on 2012-01-19
> **briancb said:**
> Ok, sorted one problem you cannot use the Logitec Cam alongside a wireless mouse and keyboard. Used a standard mouse etc. and webcam works perfect. Now I have to sort out the distorted sound.

try a different sound driver from the VM settings

For windows i use the Alsa driver

but you may find another one works better for you such as oss or pulse, and maybe change your controller for soundblaster 16 support possibly.

Cheers

---

### Post by briancb on 2012-01-20
> **haqking said:**
> try a different sound driver from the VM settings

For windows i use the Alsa driver

but you may find another one works better for you such as oss or pulse, and maybe change your controller for soundblaster 16 support possibly.

Cheers
I have now got everything working. However using it is pretty hopeless. I thought it may be my computer isn't up to the job so I disabled everything I could in windows to improve this but to no avail. I have come to the conclusion that I haven't the bandwidth or a powerful enough computer to run it properly even though I have dual core 3GHz processor and 4GB mem. So I am afraid it is back to Windows.:(

---

### Post by haqking on 2012-01-20
> **briancb said:**
> I have now got everything working. However using it is pretty hopeless. I thought it may be my computer isn't up to the job so I disabled everything I could in windows to improve this but to no avail. I have come to the conclusion that I haven't the bandwidth or a powerful enough computer to run it properly even though I have dual core 3GHz processor and 4GB mem. So I am afraid it is back to Windows.:(

Your bandwidth will be the same booting into windows, using Ubuntu or in a VM, your OS has nothing to do with your bandwidth.

4Gb mem is more than enough to run a VM.

If it works directly on the same computer with a HDD install of Windows, then there is no reason it wont in a VM, unless it is a graphical/video issue which it maybe, but video conferencing works fine for me in a VM in various applications

But whatever works for you or you can make work.

Peace

---

