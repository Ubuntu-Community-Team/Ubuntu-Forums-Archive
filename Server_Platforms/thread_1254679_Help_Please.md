---
title: "Help Please"
date: 2009-08-31
forum: Server Platforms
---

### Post by gbsemarat on 2009-08-31
Hi all. 

Im new here and I would like to take this opportunity to say a big HELLO to everyone.

I have a strange setup here and I was wondering if the following would be possible.

[IMG]http://i26.tinypic.com/zvws2a.jpg[/IMG]

I have an adsl broadband router (a linksys one) and the problem is its behind a wall where I am not allowed to do any cabling through the wall. 

On the other side of the wall I am able to recieve a good wireless signal but no signal downstairs.

Ive got one network printer, a network camera and two pcs running winxp and a network swtich, all this stuff is in the room downstairs

I was wondering if its possible to share this wireless internet connection using the ubuntu server machine on the top floor with the hardware below so that any device I connect to the switch, it will be directly connected to the internet?

I am able to get a lan cable between the two floors.
Awww shucks ... this is hard to explain but perhaps the picture attached helps.

Also, would the server be capable of directing any print jobs from the winxp pcs to the printer?

Can anyone guide me here?

---

### Post by Bachstelze on 2009-08-31
Sharing the connection is very possible, I'm writing this on such a setup. I can't tell you anything about the printer and camera, though.

---

### Post by gbsemarat on 2009-09-01
Thanks for your reply.

Could you perhaps guide me as to how I can go about sharing the internet connection for my case?

---

### Post by eylisian on 2009-09-01
If I'm not mistaken you'll need bridge-utils and then you'll need to bridge the wireless interface to the wired interface. After that you'll need to enable forwarding of traffic... Ah-ha!

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Looks like it covers what you need, you'll have to alter things for your topography.

Hope it goes well enough.

Regards.

---

### Post by Bachstelze on 2009-09-01
> **gbsemarat said:**
> Thanks for your reply.

Could you perhaps guide me as to how I can go about sharing the internet connection for my case?

[This]("http://www.gentoo.org/doc/en/home-router-howto.xml") is the guide I used. Of course, since it is for Gentoo, there is a few things you'll have to change to make it work in Ubuntu (for example, skip the kernel configuration step, and use apt-get instead of emerge to install software).

---

### Post by gbsemarat on 2009-09-01
Thanks guys...Im new to all this so Ill give it a shot and update you on how things progress :)

---

### Post by tomBorgia on 2009-09-01
Powerline Ethernet?

---

### Post by gbsemarat on 2009-09-01
I havent heard of powerline ethernet but after looking it up on wikipedia I dont think it will work.

I think the wiring on one side of the wall is seperate from the other side.
Maybe there is a connection somewhere but might be at a transformer 300 meters away...no idea

---

### Post by bobbob1016 on 2009-09-01
I'd vote to try powerline ethernet.  The nice thing is it is constant, wireless can have issues due to interference, and might be slightly unstable.  Powerline Ethernet is just ethernet as far as your computers care.  I'd suggest this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122233](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122233)

I was going to suggest an 85mbps one, but it is $2 cheaper than the "200mbps" one I suggested.  The faster mbps might give you more range.  Just don't hook this up through a powerstrip, plug it in right to the wall.  I would say try it, and return it if it doesn't work.

Edit:  Actually, the 85mpbs ones have a 4-port switch built in, might be worth trying.  [http://www.newegg.com/Product/Product.aspx?Item=N82E16833122328](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122328)

---

### Post by tomBorgia on 2009-09-01
> **gbsemarat said:**
> I havent heard of powerline ethernet but after looking it up on wikipedia I dont think it will work.

I think the wiring on one side of the wall is seperate from the other side.
Maybe there is a connection somewhere but might be at a transformer 300 meters away...no idea

Yep - if they're separate it won't work! :)

---

### Post by gbsemarat on 2009-09-01
> **tomBorgia said:**
> Yep - if they're separate it won't work! :)

Poopy! Wish I could find someone who would lend me some powerline adapters ;)

---

