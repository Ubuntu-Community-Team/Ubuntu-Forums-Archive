---
title: "wireless..y cant we get it right ????"
date: 2009-02-12
forum: Testimonials &amp; Experiences
---

### Post by sneeks on 2009-02-12
ok,have just d/l the new distro for hardy heron 8.04.2 thinking wireless would be sorted by now as im getting bored trying to find new usb dongles that work with it.
i picked up 6 belkin 7050 e's really cheap,thinking they would use the same chip....but to my horror they dont,bummer..
so after a few beers i d/l the new open susse 11 just to see if it's changed much.
guess what,nearly all the dongles i have work with no problem....
so my question is..............
why cant Ubuntu have this support..??

---

### Post by wolfen69 on 2009-02-12
since i don't see too many developers around here, you're better off asking at Launchpad.  [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

but in my own experience, i've found ubuntu very good at wireless detection. and i'm talking more than a few laptops. besides, you can always use ndiswrapper to get them going if need be.

if ubuntu supported 99.99999% of all hardware out there, the people that had the .000001% of hardware that didn't work, would come in here and say, "why can't they get it right?" it's a no-win situation. but don't worry, it's getting better all the time.

---

### Post by solwic on 2009-02-12
> **sneeks said:**
> ok,have just d/l the new distro for hardy heron 8.04.2 thinking wireless would be sorted by now as im getting bored trying to find new usb dongles that work with it.
i picked up 6 belkin 7050 e's really cheap,thinking they would use the same chip....but to my horror they dont,bummer..
so after a few beers i d/l the new open susse 11 just to see if it's changed much.
guess what,nearly all the dongles i have work with no problem....
so my question is..............
why cant Ubuntu have this support..??

My best guess would be that the software that makes them work is proprietary, since Novelle is in bed with Microsoft.  Ubuntu's philosophy, which is restrictive to the point of absurdity sometimes (IMO), prohibits the bundling of proprietary software in their ISOs.  

You could probably make them work with Ubuntu, but it won't be OOTB.

---

### Post by lancest on 2009-02-13
I never have problems connecting to WIFI with my Ubuntu notebook at the local McDonalds (and Starbucks). The other day two Vista notebook users showed up to McD and they couldn't connect to the free WIFI at all. I told them I was currently connected using Linux- no problem. Then I asked the manager to restart the router for the poor slobs.

---

### Post by stchman on 2009-02-13
> **sneeks said:**
> ok,have just d/l the new distro for hardy heron 8.04.2 thinking wireless would be sorted by now as im getting bored trying to find new usb dongles that work with it.
i picked up 6 belkin 7050 e's really cheap,thinking they would use the same chip....but to my horror they dont,bummer..
so after a few beers i d/l the new open susse 11 just to see if it's changed much.
guess what,nearly all the dongles i have work with no problem....
so my question is..............
why cant Ubuntu have this support..??

It is common for wireless card makers to use COMPLETELY different chipsets on the same model card.  They simply give it a different rev.

I have found that Intel and Atheros wireless cards are the best choice for Linux.

---

### Post by Crafty Kisses on 2009-02-13
I agree with stchman, Intel and Atheros work great, I'm pretty sure Belkin has always had problems.

---

### Post by solwic on 2009-02-13
> **Codename said:**
> I agree with stchman, Intel and Atheros work great, I'm pretty sure Belkin has always had problems.

+1.  Belkin is pretty much junk for wireless in Ubuntu.

---

### Post by JK3mp on 2009-02-13
Belkin is pretty much useless in ANY os,lol...linksys actually do pretty good as far as routers go with linux..from what i've experienced..

---

### Post by solwic on 2009-02-13
> **JK3mp said:**
> Belkin is pretty much useless in ANY os,lol...linksys actually do pretty good as far as routers go with linux..from what i've experienced..

I have a Linksys router and it works great.  I also tried a Linksys wireless card in my desktop pc, and it wasn't bad once I figured out ndiswrapper.  :)

---

### Post by Crafty Kisses on 2009-02-14
I'd also think this would be a great time and say, do some research before you buy a card, you know. It's not all that hard to do. Remember Google is your friend.

---

### Post by solwic on 2009-02-14
> **Codename said:**
> I'd also think this would be a great time and say, do some research before you buy a card, you know. It's not all that hard to do. Remember Google is your friend.

That's the thing, though.  If you look on the hardware compatibility list at the Ubuntu wiki, you'll see the WMP54G wireless v 4.1 (I think...whichever the latest 4.x is) listed as functional...but it isn't, unless you install the Windows drivers.  

You can research, but most of the lists out there are wrong.  The ATI X1300 is listed for functional 3D support, but it doesn't mention you only get that if you disable composite rendering.  

The lists are either flat wrong or incomplete.  :(

</complain>

---

### Post by 3rdalbum on 2009-02-14
> **Codename said:**
> I'd also think this would be a great time and say, do some research before you buy a card, you know. It's not all that hard to do. Remember Google is your friend.

Good idea. I bought a motherboard with inbuilt wireless after checking a compatibility list. It worked fine from Gutsy to Hardy, and then there was a regression that caused terribly low signal strength in Intrepid. Fortunately there's another driver that can be used, but there's got to be something wrong with wireless support if things can go belly-up in a new kernel.

---

### Post by calrogman on 2009-02-16
> **sneeks said:**
> ok,have just d/l the new distro for hardy heron 8.04.2 thinking wireless would be sorted by now as im getting bored trying to find new usb dongles that work with it.
i picked up 6 belkin 7050 e's really cheap,thinking they would use the same chip....but to my horror they dont,bummer..
so after a few beers i d/l the new open susse 11 just to see if it's changed much.
guess what,nearly all the dongles i have work with no problem....
so my question is..............
why cant Ubuntu have this support..??

Because some manufacturers neither
A) provide Linux drivers (open-source or not)
or
B) release hardware specifications.

Good day.

---

### Post by sneeks on 2009-02-17
well thanks for all the feedback chaps,it was good to get all the responses,and yes google can be your friend,and yes novelle is in that big bed !!!!!,which is probably y u have to click yes to the eula after install.
on another note though,although open susse ran ok it really wants 1gig of ram,not my cup of cha im afraid..
sneeks.

---

### Post by mdsmedia on 2009-02-17
I sometimes wonder how much effort people put into getting wireless working in Ubuntu.

I'll say right from the start, I'm no IT pro or expert or geek. Whenever I re-install Ubuntu I find my Wireless doesn't work. I fiddle and play and coax, and it won't work. Then all of a sudden, something I fiddle with gets Wireless working. I wish I took more notice of what I was doing :idea:.

---

### Post by solwic on 2009-02-17
> **mdsmedia said:**
> I sometimes wonder how much effort people put into getting wireless working in Ubuntu.

I'll say right from the start, I'm no IT pro or expert or geek. Whenever I re-install Ubuntu I find my Wireless doesn't work. I fiddle and play and coax, and it won't work. Then all of a sudden, something I fiddle with gets Wireless working. I wish I took more notice of what I was doing :idea:.

It took me about an hour of back-and-forth with Codename to get my wireless working.  Of course, I did a little research before I went and bought the PCI card, too.  :)

---

### Post by mdsmedia on 2009-02-17
When I last re-installed, a few weeks ago, I plugged in an ethernet cable because wireless wasn't working. I did what I wanted to do, wired, but I wanted to be able to move my notebook off my desk.

I took it and sat in the lounge, unconnected, and fiddled with wireless and all of a sudden it just worked.

I suppose I knew it worked and it was just a matter of holding my tongue the right way, but for the life of me, except for the first time I installed, 5.04, it hasn't just worked upon install. But I knew it worked.

Others probably THINK their wireless doesn't work because they haven't experienced it working, yet.

---

### Post by 3rdalbum on 2009-02-18
I've seen some newbies who thought their wireless wasn't working, literally because Ubuntu didn't automatically connect to their home network... I mean, how could Ubuntu possibly know which network is theirs? Having said that, we would tend to say "Go to Network Manager and see if there are any networks available" but a new user wouldn't know that the two little computer icons actually are anything to do with networking.

---

