---
title: "Using gsynaptics..."
date: 2006-08-22
forum: System76 Support
---

### Post by Kaloma on 2006-08-22
I just received my Serval Performance today and... wow!  Terrific product, Ubuntu is very nice, and everything works as expected.

I am not very accustomed to touchpads, and I find the tap-sensitivity of this pad a bit high.  I am frequently unintentionally tapping, causing funny things to happen.

I installed gsynaptics, manually added the requisite line to my xorg.conf, and finally added gsynaptics-init to my startup programs.  After restarting the X server, I gsynaptics still fails to run, with the message:
[QUOTE="Error dialog"]GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics[/QUOTE]
Is there something else that I am missing here, something that is not in the README?

My xorg.conf is attached. (Is there a way to attach this file on these forums without giving it some silly extension?)

Thanks in advance,
Matthew

---

### Post by crichell on 2006-08-22
Hello Kaloma,

Actually the Serval doesn't use a Synaptic touchpad.  I haven't found a tool for adjusting it yet but we're looking for a good one.  I don't remember the touchpad manufacturer off the top of my head but I'll post tomorrow once I'm back at the office.

Cheers, Carl

---

### Post by crichell on 2006-08-23
Hi Matthew - the touchpad is by ElanTech.  I'll be looking for a tool to configure it's features.  Let me know if you find anything as well.

Carl

---

### Post by uttaranduutta on 2007-03-25
Hello Carl
I think before we can make a app to change the working of the Touchpad in run time we would have to driver a driver for it, currently the Elanyech touchpad emulated a PS/2 mouse.
Thankyou 
Uttaran

---

### Post by uttaranduutta on 2007-03-25
Hello Carl
I think before we can make a app to change the working of the Touchpad in run time we would have to driver a driver for it, currently the Elantech touchpad emulates a PS/2 mouse.
Thankyou 
Uttaran

---

### Post by crichell on 2007-03-26
You're right - we can't modify sensitivity, scrolling or things like that.  We should be able to put together a simply utility to disable and enable the ElanTech - by rmmod psmouse/modprobe psmouse.  An external USB or bluetooth mouse works with the psmouse module removed.  It's the best option I've come up with so far - I'm open to any sugestions.

---

### Post by deepak_theidiot on 2007-08-13
hi members am having LG XNOTE G1 325LA2 but broke my mainboard cd...can any one send me the link wer can i downlad it pls... my mail id is [email]deepakost@gmail.com[/email]

---

### Post by Tomone on 2007-08-18
Is it the same touchpad on all of your laptops? Because I have a new Pangolin and am having the same problem in trying to configure it.

---

### Post by nicedream on 2007-08-19
> **Tomone said:**
> Is it the same touchpad on all of your laptops? Because I have a new Pangolin and am having the same problem in trying to configure it.

Yes, I am curious about this too.  What kind of touchpad is used on the Gazelle value?

---

### Post by thomasaaron on 2007-08-20
The Gazelle uses the Synaptic touchpad.

---

### Post by Tomone on 2007-08-21
Does the Pangolin use a different touchpad?

---

### Post by thomasaaron on 2007-08-21
The new Pangolin uses an Elan Tech touchpad.

---

### Post by alanandhispc on 2007-08-22
I have a MSI M660 with an elantech touchpad and i've sent countless emails to elantech asking for either details or a linux driver and so far the only thing i've got from them is:

"We don't have a linux driver, sorry"

they won't say anything other than this each time, even when i ask for an explanation, granted, they are based in the far east, but i've come to expect some decent response about linux in the past year or so.

based on their site, it looks like it uses a number of patents found in synaptics touchpads, just wondering if the synaptics drivers could be hacked to pickup the elantech hardware also. but you could only assume something like this if they would just respond to confirm the similarities....happy days

any thoughts from anyone else? maybe system76 could offer some backing by contacting elantech or whoever it is they use as a ODM.


Thanks,


Alan

---

### Post by thomasaaron on 2007-08-22
You can disable the touchpad with:

sudo rmmod psmouse

You can restore it with:

sudo modprobe psmouse


I'm writing a little Python app that will do the job. It will come out in the next driver.

---

### Post by alanandhispc on 2007-08-23
yeah i've been doing that for a while now, but it still doesn't excuse elantech from being so unfriendly towards Linux.

What makes it so hurtful is they run linux for their email server, or at least the company they use for email does.

Has any one else pestered elantech? they've stopped replying to my emails now. (only sent about 4 asking for hardware details or a linux driver)

[http://www.elantech.com.tw/003/index.aspx](http://www.elantech.com.tw/003/index.aspx)

---

