---
title: "Virtualbox No faster than live CD"
date: 2009-11-12
forum: Virtualisation
---

### Post by Plumtreed on 2009-11-12
I used Fedora 11 iso to try Virtualbox for the first time. I was surprised by just how slow the whole process is. It works but it takes longer to load than the the basic live CD. 

Once loaded it just doesn't seem any better than running the live CD 

The screen size appears to be firmly fixed at about 800x600 which i imagine can be sorted?

Am I missing something?

---

### Post by sdowney717 on 2009-11-12
i like vmware player 3.0
you can create and edit vm's

with virtualbox you need to run the extensions just like you need in vmware.

and you can resize the screen to full size. the issue here is cpu and motherboard power. 
weak cpu will give you a very poor vm experience.

---

### Post by Plumtreed on 2009-11-12
No it is not a 'monster'; Celeron 560@2.13GHZ and 1GB Ram on a Laptop.

OK I guess I have to have a second rate result on VirtualBox!

Thanks

---

### Post by Simian Man on 2009-11-12
With 1 gig of RAM, you probably give the VM what 512?  I'm not surprised that running as a LiveCD with 1 gig gives better results.

---

### Post by jflaker on 2009-11-12
> **Plumtreed said:**
> No it is not a 'monster'; Celeron 560@2.13GHZ and 1GB Ram on a Laptop.

OK I guess I have to have a second rate result on VirtualBox!

Thanks

Add ram and you will see a difference....

---

### Post by Plumtreed on 2009-11-12
I need more 'physical' ram added to my machine like 2GB total or just assign more?

---

### Post by andrew.46 on 2009-11-13
Hi Plumtreed,

> **Plumtreed said:**
> I need more 'physical' ram added to my machine like 2GB total or just assign more?

I have just increased the ram on my laptop from 1GB to 2GB and the big winner was the guest machines in Virtualbox. I now allocate 512MB to each of three virtual machines (Windows XP, Hardy Heron and Kamic Koala) and while running the host distro (slackware 13) I can comfortably run all three guests at the same time. While I rarely actually do this I will admit to doing it primarily to test the ram upgrade :). So my thought would be: more physical ram.

Andrew

---

### Post by Plumtreed on 2009-11-13
That is impressive and it sounds like it would be worthwhile adding another 1GB.....should have done that long ago anyhow. 

I do run the guest at 512 but that is 'painful'! How comfortable is the speed with the extra RAM?

---

### Post by andrew.46 on 2009-11-13
Hi Plumtreed,

> **Plumtreed said:**
> I do run the guest at 512 but that is 'painful'! How comfortable is the speed with the extra RAM?

I guess ram is only one consideration and another would be processor speed and yet another vital point would be what you are trying to accomplish in each of the VMs. It would be foolish to run a big compile job on all 4 open distros at the same time and games would be a similar issue. But extra ram gives you the option of for example running one guest vm only and allocating 1GB of ram to it, this is closer to what I would personally be doing and VirtualBox allows for this kind of flexibility. Having 4 operating systems open at one time is just a demonstration, but one that certainly proved to me that extra ram with VirtualBox is an excellent idea :).

All the best,

Andrew

---

### Post by snowpine on 2009-11-13
> **Plumtreed said:**
> I used Fedora 11 iso to try Virtualbox for the first time. I was surprised by just how slow the whole process is. It works but it takes longer to load than the the basic live CD. 

Once loaded it just doesn't seem any better than running the live CD 

The screen size appears to be firmly fixed at about 800x600 which i imagine can be sorted?

Am I missing something?

Hi Plumtreed, do I understand your post correctly? You are running the Fedora 11 .iso in "Live CD" mode, within VirtualBox running in an Ubuntu host? 

If that is correct, remember that running in "Live" mode is always slower than once you install. So, you will see a boost in performance once you install Fedora within the virtual machine.

Right now, what you are basically doing is running a Live CD (slow) on a virtual computer with only half the ram of your computer (slower).

Does that make sense?

I am not sure about the resolution issue. Have you tried installing the Guest Additions?

Also remember that Fedora is a "heavy" full featured distro. Try Puppy or SliTaz in the VM if you want to be impressed.

---

### Post by Plumtreed on 2009-11-13
Oh Wow, Now I get it........how dumb is that!

Thanks Snowy, Andrew, I have added another GB of RAM and did a proper install. It is just fantastic!

I appreciate your help.

---

### Post by andrew.46 on 2009-11-13
Hi Plumtreed,

> **Plumtreed said:**
> Thanks Snowy, Andrew, I have added another GB of RAM and did a proper install. It is just fantastic!

Excellent news, I hope you now fully enjoy this amazing program :). As a side note good to see yet another fellow Australian on these Forums!

Andrew

---

### Post by Shazaam on 2009-11-13
Plumtreed...
Be sure to install the Guest Additions in the guest (not the host). And if you want a little more speed from your virtual machines put them on a separate internal hard drive.

---

### Post by Plumtreed on 2009-11-14
> **andrew.46 said:**
> Hi Plumtreed,



Excellent news, I hope you now fully enjoy this amazing program :). As a side note good to see yet another fellow Australian on these Forums!

Andrew

I was aware that VirtualBox was available but thought it would be too complex. Now, I have to control the urge to try everything.

Aussies get everywhere don't they;)

---

### Post by Plumtreed on 2009-11-14
> **Shazaam said:**
> Plumtreed...
Be sure to install the Guest Additions in the guest (not the host). And if you want a little more speed from your virtual machines put them on a separate internal hard drive.

Thanks Shazaam, I did as you suggested but I admit by good luck rather than good management! Appreciate your confirmation that this was the better road to take.

---

### Post by andrew.46 on 2009-11-14
Hi Plumtreed,

> **Plumtreed said:**
> Aussies get everywhere don't they;)

Which is how it should be :). But it is such a strange coincidence that we are both Australians running VirtualBox and also in the process of upgrading ram on laptops by 1gig! Mine is a slightly elderly Dell Latitude D520 and the ram was a single 1gig Kingston chip that I bought online from [Ramcity]("http://www.ramcity.com.au/system/29920.htm"). It has been a while since I bought ram and I was more than a little surprised at the low cost, and this was Kingston brand which I know costs a little more. In terms of VirualBox definitely a fine investment.

All the best,

Andrew

---

### Post by Plumtreed on 2009-11-14
Getting the back off the Laptop wasn't as easy as suggested but we got there. 

I am glad I added the RAM but it really wasn't essential because I found that the few applications I have tried go well enough on marginal RAM when properly installed.

---

