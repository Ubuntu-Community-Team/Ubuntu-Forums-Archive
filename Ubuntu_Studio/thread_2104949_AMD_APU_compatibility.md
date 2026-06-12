---
title: "AMD APU compatibility"
date: 2013-01-14
forum: Ubuntu Studio
---

### Post by DracoMaille on 2013-01-14
I have just purchased a new laptop and I want to be as sure as I can be that Ubuntu Studio will work properly with it.  New hardware (not yet delivered as of this posting): 
   Toshiba Satellite  L870D-BT3N22
   AMD Quad Core A10 4600 APU 2.3GHz (3.2GHz Turbo boost 3.0) processor
   4 GB DDR3 1600
   640 GB HDD

Most importantly, what I am trying to find out is whether the APU architecture will work properly with the Ubuntu Studio 12.10 in light of the lack of a stand-alone CPU and GPU.  Considering the success I have had working with Ubuntu on several previous computers I assume that the OS is intuitive enough to understand the chip architecture ... but before I cause myself a headache trying to fit a square peg into a round hole I should ask:  

1.  Are there any known issues running Ubuntu Studio 12.10 on an AMD APU?  
2.  If there are known issues, is there a simple work-around (i am still a novice with Linux) or would I be better off starting with a different distro?  
3.  Are there any specific procedures for optimizing this distro to maximize the efficiency of my new hardware?

---

### Post by coffeecat on 2013-01-14
> **DracoMaille said:**
> 
1.  Are there any known issues running Ubuntu Studio 12.10 on an AMD APU?

Probably not. I'm using an AMD A6 3500 three-core APU in a desktop machine. Although I prefer to use a separate graphics card, I did try booting up standard Ubuntu 12.10 without a PCIe graphics card and using the APU graphics and it worked just fine with the default open source video driver. The fact that you are running Ubuntu Studio should not make any difference.

**EDIT**: boot up with the live DVD and see if it works. If it does, you should be OK. It's a good way of testing compatibility without committing yourself to a permanent installation.

---

### Post by DracoMaille on 2013-01-15
Sounds good ... I didn't think there would be any real problems with it ... .Ubuntu has always treated me well.  

Is there anything simple I can do to make sure I am getting max performance out of the hardware?  I know Ubuntu generally optimizes itself ... but with new hardware sometimes there is a little tweak here or there that can boost performance pretty significantly.  I don't want to get too complex right off the bat, but if there's a package that anyone knows about that will maximize hyperthreading efficiency or something like that, I'd appreciate a point in the right direction.  

By the way ... I am still waiting on the delivery of my new system ... just trying to get a head start on any issues that might arise.  I will keep this thread open until the hardware comes in and I can get it up and running right.  

Either way, thanks for your time.  Have a good day :-)

---

### Post by DracoMaille on 2013-01-22
Just got the laptop in the mail ... installed Ubuntu (gnome) 12.10 64 bit ... seems everything is working fine, except I am having an issue with the laptop not waking up after suspend (close lid, reopen and screen stays blank.  Power button doesn't turn computer on ... have to hard boot, but then everything works just fine again.  I know I have already seen a fix for this somewhere on these forums, but I forget exactly where.

so yeah ... ubuntu DOES work with the new 4 core A10 from AMD (integrated graphics and all)

---

### Post by khatkarrohit on 2013-02-07
Can you post benchmark result for your AMD A10 processor. There is a package in ubuntu software center. I am also planning to buy a [laptop]("http://www.flipkart.com/hp-pavilion-g6-2313ax-laptop-apu-quad-core-a10-6gb-1tb-dos-2-5gb-graph/p/itmdh954sn9dchzf?pid=COMDH93QMXNH7U2W") with the same processor. But some people say that AMD is not good.:confused:

---

### Post by mastablasta on 2013-02-07
regarding graphics it is better than intel.

---

### Post by ttoine on 2013-02-07
Hum, 12.10 should be fine, but think that for 12.04 LTS, the free AMD driver is not recent enough for HD7000 and up (integrated in hte new AMD A6, A8 and A10).

If for any purpose you need high Open GL performance, add the X-egers PPA. maybe it could fix the problem of waking up.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by gscheben on 2013-05-13
> **DracoMaille said:**
> Just got the laptop in the mail ... installed Ubuntu (gnome) 12.10 64 bit ... seems everything is working fine, except I am having an issue with the laptop not waking up after suspend (close lid, reopen and screen stays blank.  Power button doesn't turn computer on ... have to hard boot, but then everything works just fine again.  I know I have already seen a fix for this somewhere on these forums, but I forget exactly where.

so yeah ... ubuntu DOES work with the new 4 core A10 from AMD (integrated graphics and all)

DracoMaille, did you ever resolve this issue of "ubuntu not waking up after screen open on laptop"? I have an HP laptop that uses the A8 apu and I have the same issue. Struggling to find a solution, any advice?

---

