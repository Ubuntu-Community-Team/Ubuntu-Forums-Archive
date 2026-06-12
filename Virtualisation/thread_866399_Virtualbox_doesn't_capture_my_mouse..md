---
title: "Virtualbox doesn't capture my mouse."
date: 2008-07-21
forum: Virtualisation
---

### Post by kramer65 on 2008-07-21
Hello,

I just installed virtualbox and am now installing windows on it. However, when I click the host button (right Ctrl) it says it captured the mouse (shows green arrow icon) but it actually isn't. I still see two mouse pointers and the one in the windows installation doesn't move at all..

Does anybody know a solution to this?

---

### Post by alzie on 2008-07-21
If you click inside your virtualbox, it should "take" your mouse.

Hitting rt ctrl releases your mouse to your Ubuntu again.

I think this is what you are looking for.

---

### Post by Joeb454 on 2008-07-21
+1 I find just clicking in the VM is the easiest way to get my mouse in there.

---

### Post by kramer65 on 2008-07-21
Yeah I tried that as well. When I click however, I first get the message saying it will be captured, after which I click "capture". But nothing happens. I see the green arrow icon in the right bottom corner, but I also still see two mouse pointers and the one in MS windows is not moving. I am by now logged into windows, but can't use it.. :(

Arent there any settings or something in which this needs to be set? I am using compiz in normal ubuntu installation. Maybe that has something to do with it?

Any other ideas that might help?

---

### Post by Joeb454 on 2008-07-21
Hmm, od, it should just capture your mouse when you click inside the VM. Try disabling compiz and see if it persists...I doubt compiz would affect it, but it can't hurt to try ;)

---

### Post by Sinkingships7 on 2008-07-22
Odd... I went to go use virtualbox today, and though I've never had any issues in the past with it, it's suddenly doing exactly what the OP stated.

---

### Post by runbei on 2008-08-02
This is a known problem with VirtualBox (at least in version 1.6.4 and the OSE versions). I haven't been able to find an answer - so far just others reporting the same issue on the VirtualBox forum.

---

### Post by bumanie on 2008-08-02
I have had the same problem with every version of virtualbox since version 1.5.4 Version 1.5.4 works fine. Never tried the 1.6.4, but versions 1.5.6 and 1.6.0 wouldn't work for me. I just stick with 1.5.4 and everything is fine.

---

### Post by runbei on 2008-08-02
I found the solution and thought I would post it here for others to see.

Briefly, what worked for me is to go ahead and install XP even though I was unable to use the mouse. I found it was possible to complete all of the installation steps using the Tab and cursor arrow keys.

Once XP was installed, I could run XP and use the Devices toolbar menu to install the Virtual Box Guest Additions. This involves two steps: first mount the Guest Additions .iso file from the Device menu. And then choose the option on the Device menu to install the Guest Additions. When you're done, shut down XP, log out and back in, and you'll be able to use the cursor in the VirtualBox window normally - when you move the cursor into the window you can use the mouse to work with Windows XP as expected.

It's a good idea to consult the VirtualBox manual while completing these steps - especially the part about being sure you have the proper software installed that VirtualBox needs - sorry, I forget what they're called, something like SDK and DKMS?? (I'm running Windows this morning and don't have access to the manual.) This is a simple process that you do in a terminal - the steps are described at the top of the section in the manual on installing the VB Guest Additions.

---

### Post by cozmicharlie on 2008-08-03
Thanks for the how to. Works great.  However, in doing this I stumbled across a way to fix this.  When you click in VBox and the capture dialog comes up it also gives you an option to "not show this message again" - check this, press capture and the mouse should now work.  At least it did for me.

---

### Post by kramer65 on 2008-08-04
Grrrrrrrreat!!I did everything everybody said, EXCEPT for clicking the option "not to show the message again". But now it works miraculasly!!

Thanks!

---

### Post by jamespi on 2008-09-17
yeah - just clicking "dont show this message again" solves the problem for me too.

i dont think you have to bother with all that additions CD stuff - at least try the "dont show the message" thing first.

---

### Post by elsaturnino on 2008-09-30
Clicking on the "do not show this message again" box worked like a charm. (I'm running VirtualBox 2.0.2)

---

### Post by 10gallons on 2008-10-02
> **elsaturnino said:**
> Clicking on the "do not show this message again" box worked like a charm. (I'm running VirtualBox 2.0.2)

Yep, x2 same setup. Thanks.

---

### Post by Kilobyte on 2008-10-22
The unchecking of the box worked for me.
Thanks!

---

### Post by randini100 on 2009-01-19
Cozmicharlie's post of Dec 2007 fix works just fine!

With Intrepid Ibex and virtualbox 2.10  running XP in the box.  Clicked on don't show this message again.... poof! all is well

---

### Post by boof1988 on 2009-01-23
> **cozmicharlie said:**
> Thanks for the how to. Works great.  However, in doing this I stumbled across a way to fix this.  When you click in VBox and the capture dialog comes up it also gives you an option to "not show this message again" - check this, press capture and the mouse should now work.  At least it did for me.

Thank You!!!
Thank You!!!
Thank You!!!

This is the first post (that I have stumbled upon) to give this solution.  I'm just learning how to use VirtualBox and was getting very frustrated because I couldn't even install some OS (I can't remember which one) in VM because there was no assigned-letter for the final install button needed to actually do the install.  This would have not been such a problem, but posts I have seen say to install the guest additions... but... the OS has to be installed to use them.

Thanks again for the solution.

---

### Post by cozmicharlie on 2009-01-23
> **boof1988 said:**
> Thank You!!!
Thank You!!!
Thank You!!!

This is the first post (that I have stumbled upon) to give this solution.  I'm just learning how to use VirtualBox and was getting very frustrated because I couldn't even install some OS (I can't remember which one) in VM because there was no assigned-letter for the final install button needed to actually do the install.  This would have not been such a problem, but posts I have seen say to install the guest additions... but... the OS has to be installed to use them.

Thanks again for the solution.

Glad to hear it helped you.
It's always nice to find a simple solution to an annoying problem.

---

### Post by alscorpion on 2009-03-27
Well I've had this problem since I've started using virtual box and I think **[SIZE="4"]cozmicharlie[/SIZE]** had got it! 

I've tried everything until using this method. It's easy!! just check the "Don't show this massage again" 

Thanks cozmicharlie

---

### Post by boof1988 on 2009-03-27
> **alscorpion said:**
> Well I've had this problem since I've started using virtual box and I think **[SIZE="4"]cozmicharlie[/SIZE]** had got it! 

I've tried everything until using this method. It's easy!! just check the "Don't show this massage again" 

Thanks cozmicharlie

Three cheers for cozmicharlie!

:popcorn: :popcorn: :popcorn:

---

### Post by JockVSJock on 2009-10-24
I was having the same issue too and did what was recommended. 

thanks

---

### Post by omniinst on 2012-11-01
After fighting with this all morning I moved the VM from my secondary display over to my primary and voila!  Not sure if this is the cause for anyone else's woes, but VirtualBox is capturing my mouse with no problems now.  Really odd little glitch.  Can't believe I was pulling my hair out over that one!

---

