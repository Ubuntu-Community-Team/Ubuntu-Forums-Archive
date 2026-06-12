---
title: "has this ubuntu developer blog been discussed yet?"
date: 2009-10-16
forum: The Cafe
---

### Post by sdowney717 on 2009-10-16
[http://www.fewt.com/2009/10/i-give-up.html](http://www.fewt.com/2009/10/i-give-up.html)

this is the one where he says he gives up.

---

### Post by doas777 on 2009-10-16
<sigh>
why is it that OSS developers only ever make press when they are ranting about it being everyone elses fault...
</sigh>

---

### Post by steeleyuk on 2009-10-16
I read about this on Reddit. 

I came to the conclusion that its up to him what he does. With the number of people working on Ubuntu and the number of people using it, you don't often hear about things like this, so there can't be too much wrong with it.

---

### Post by fewt on 2009-10-16
> **doas777 said:**
> <sigh>
why is it that OSS developers only ever make press when they are ranting about it being everyone elses fault...
</sigh>


Maybe because no one listens otherwise.  I think there is enough evidence in my article to support my conclusion, and I could add more though like eeepc-laptop hard coding function key functions rather than passing them to the ACPI handler so their functions can be altered to do what the USERS want rather than what the kernel module maintainer wants.

```

static struct key_entry eeepc_keymap[] = {
        /* Sleep already handled via generic ACPI code */
        {KE_KEY, 0x10, KEY_WLAN },
        {KE_KEY, 0x12, KEY_PROG1 },
        {KE_KEY, 0x13, KEY_MUTE },
        {KE_KEY, 0x14, KEY_VOLUMEDOWN },
        {KE_KEY, 0x15, KEY_VOLUMEUP },
        {KE_KEY, 0x1a, KEY_COFFEE },
        {KE_KEY, 0x1b, KEY_ZOOM },
        {KE_KEY, 0x1c, KEY_PROG2 },
        {KE_KEY, 0x1d, KEY_PROG3 },
        {KE_KEY, 0x30, KEY_SWITCHVIDEOMODE },
        {KE_KEY, 0x31, KEY_SWITCHVIDEOMODE },
        {KE_KEY, 0x32, KEY_SWITCHVIDEOMODE },
        {KE_END, 0},
};

```

In order to make the left most silver key disable the touchpad, one must fork the module and comment out key 0x1a.  The need for this is just silly.

Perhaps we can discuss changing the SHE interface from "she" to "cpufv" from 2.6.29 to 2.6.30.  I can go on, and on, and on.

---

### Post by Bachstelze on 2009-10-16
> **doas777 said:**
> <sigh>
why is it that OSS developers only ever make press when they are ranting about it being everyone elses fault...
</sigh>

This.

---

### Post by doas777 on 2009-10-16
> **fewt said:**
> Maybe because no one listens otherwise.  I think there is enough evidence in my article to support my conclusion, and I could add more though like eeepc-laptop hard coding function key functions rather than passing them to the ACPI handler so their functions can be altered to do what the USERS want rather than what the kernel module maintainer wants.
In order to make the left most silver key disable the touchpad, one must fork the module and comment out key 0x1a.  The need for this is just silly.

Perhaps we can discuss changing the SHE interface from "she" to "cpufv" from 2.6.29 to 2.6.30.  I can go on, and on, and on.

I am completely with you on named constants. changes to them should not be undertaken lightly, but often are, in any programming environment. this is not a problem unique to linux, nor to the ubuntu kernel.

that said, you heap some serious critisms that are not entirely supported in your rant (piles-of-excrement kind of stuff) that really helps no one reach any kind of conclusion except that you are angry. for instance, I've seen nothing indicating that these issues are specific to the ubuntu kernel. does your stuff run flawlessy in the Vanilla? 

I'm a dev as well, but probably not on your level, so I know what a pain it is to have users barking down your door, and yes I have said "Blame Microsoft" on a number of occasions, so I won't fault you for that. At the same time, is screaming "ubuntu is crap" really the correct response to problems your having enabling a such a small market  segment as a single netboot makers offerings? it seems disproportionate.

at the same time, every time one of these blogs hits /. or the register, hundreds of thousands of folks that know little of OSS beyond what they see on blogs, leave with a terrible impression of the OSS comunity, and a belief that we will simply collapse under the weight of our own spagettii code. the Linus vs Con Kolivias contraversy for instance, or Zeds rant on the rails community a few months ago, fostered nothing constructive. all they did was feed the arguments of the closed source folks. 

Now, all that said, I would like to join all the commenters on your blog, and thank you for your contributions to the community. We will be sad to see you go, and I wish you the best of luck with whatever endeavors you choose to persue. 

Best Regards, 
Franklin

---

### Post by doas777 on 2009-10-16
> **Bachstelze said:**
> This.

we've been butting heads a lot lately bachstelze. I'm beginning to think you are trolling me intentionally.

---

### Post by Bachstelze on 2009-10-16
> **doas777 said:**
> we've been butting heads a lot lately bachstelze. I'm beginning to think you are trolling me intentionally.

Er, what? Didn't I just agree with you?

---

### Post by doas777 on 2009-10-16
> **Bachstelze said:**
> Er, what? Didn't I just agree with you?
oh. ok. I guess I can read it that way. you have my apologies.

---

### Post by macogw on 2009-10-18
I just want to know how any of that is Ubuntu's fault and not the upstream kernel's fault...

---

### Post by 3rdalbum on 2009-10-18
He does raise one good point that has been mentioned before: Why did Ubuntu 9.04 ship with the Intel graphics driver in the state that it was? Were there any benefits at all, much less anything good that outweighed the terrible performance?

---

### Post by doas777 on 2009-10-19
> **macogw said:**
> I just want to know how any of that is Ubuntu's fault and not the upstream kernel's fault...

in all fairness I did attend a talk a few weeks ago by Peter Graner, the head of the kernel team, and he did reveal that ubuntus kernel is not the straight upstream stable. they cherry pick stuff from the bleeding edge, and pull it back into the stable if it looks like it works. they also clean up some staging stuff that lacks activity or demand. I'm told that the linux foundation requires ubuntu bug reports to be reproduced with a "vannilla" kernel which is just the upstream stable, before accepting.

---

### Post by doas777 on 2009-10-19
> **3rdalbum said:**
> He does raise one good point that has been mentioned before: Why did Ubuntu 9.04 ship with the Intel graphics driver in the state that it was? Were there any benefits at all, much less anything good that outweighed the terrible performance?
true, the regressions were unacceptable, but I'm told that under cannonical's pressure, Intel has been cleaning up their act a bit.

---

