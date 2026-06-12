---
title: "virtualbox gets 3d acceleration"
date: 2008-12-18
forum: The Cafe
---

### Post by toupeiro on 2008-12-18
[http://www.phoronix.com/scan.php?page=news_item&px=NjkzOA](http://www.phoronix.com/scan.php?page=news_item&px=NjkzOA)

Parallels x64 has been working towards this for the better part of a year, Vbox delivers on it!  This is big for virtualization!

---

### Post by chris4585 on 2008-12-18
this has been long awaited!

---

### Post by grazed on 2008-12-18
i just did a cartwheel.

---

### Post by jespdj on 2008-12-18
And besides that, there's a whole list of other new features! Great that Sun is working so hard on making VirtualBox even better!

---

### Post by billgoldberg on 2008-12-18
It seems Windows will get the opengl 3d acceleration first, linux will have to wait a bit longer.

But still, good news.

---

### Post by cb951303 on 2008-12-18
In their site they state that they are also planning D3D acceleration. YAY!!

---

### Post by Nevon on 2008-12-18
> **billgoldberg said:**
> It seems Windows will get the opengl 3d acceleration first, linux will have to wait a bit longer.

But still, good news.

But that's for the guest OS, right? So technically we Linux people are benefiting more from this, as there's not much of a point to virtualize Windows inside Windows. :p

But can you actually do anything with this type of 3d acceleration, or is it more of a proof of concept? Right now you can't get aero or 3d games running, right?

---

### Post by binbash on 2008-12-18
I tried it 2-3 hours ago.Tried 3-4 simple games, it does not work.However i am not sure if they are using opengl : )

---

### Post by grazed on 2008-12-18
> **binbash said:**
> I tried it 2-3 hours ago.Tried 3-4 simple games, it does not work.However i am not sure if they are using opengl : )

the older 3d games used it, or had it as an alternative before directx got popular. 

the game you're trying to run probably needs directx. but not to worry! apparently that's next on the list for virtualbox.

i'm just happy i can play counter strike 1.6 without wine now. =)

---

### Post by linuxguymarshall on 2008-12-18
:KS:guitar::p:KS:popcorn::p:guitar::guitar::guitar:

---

### Post by Dixon Bainbridge on 2008-12-18
Why not just dual boot and run the games natively?

---

### Post by cb951303 on 2008-12-18
> **Dixon Bainbridge said:**
> Why not just dual boot and run the games natively?

why reboot when you have the ability to run game instantly?

---

### Post by gn2 on 2008-12-18
It's been available in VMWare for years.

[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling.html)

---

### Post by hanzomon4 on 2008-12-18
When will I be able to run compiz/kwin in my guestOS

---

### Post by cb951303 on 2008-12-19
> **gn2 said:**
> It's been available in VMWare for years.

[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling.html)

Yes and it's experimental and disabled by default for years. And it's not officially recommended to use.

---

### Post by toupeiro on 2008-12-19
> **cb951303 said:**
> Yes and it's experimental and disabled by default for years. And it's not officially recommended to use.

Not to mention that it was never hardware based 3d acceleration.  It was software based, very buggy, and much, much slower....  But, if it was good enough for you, then kudo's!  Direct hardare acceleration has never been made available like this in a virtual guest OS with the exception of those who actually got their hands on the x64 parallels beta.  In VMWare, your video card was a virtual device, using VMWare provided drivers.  If this 3d-acceleration is truly what I think it is (Like Parallels), that means I can use a native NVidia driver for hardware based 3d acceleration in a VM.

Unfortunately, I won't get to experience this until I get my core i7.  My current processor in this machine doesn't have the Intel-VT or AMD-V extensions..

---

### Post by Trail on 2008-12-19
Very nice.

---

### Post by SupaSonic on 2008-12-19
For now it's pretty useless. Most if not all opengl games run without problems in wine anyway, and wine is very lightweight compared to virtualbox.

When support for DirectX comes, _that_ will be interesting.

---

### Post by cb951303 on 2008-12-19
> **SupaSonic said:**
> For now it's pretty useless. Most if not all opengl games run without problems in wine anyway, and wine is very lightweight compared to virtualbox.

I don't think most of the opengl games works with wine. In my experience most of them don't work and it's not such a shock since games are not only made with OpenGL but with also other SDKs, libraries and Win32 calls. Wine has to emulate(!) all of this in order to achieve a godd gaming experience. In virtualization technology, for games, developers only need to worry about hardware acceleration. In theory it's much more simpler than what Wine developers have to do hence it has more probability to work.

---

### Post by SupaSonic on 2008-12-19
> **cb951303 said:**
> I don't think most of the opengl games works with wine. In my experience most of them don't work and it's not such a shock since games are not only made with OpenGL but with also other SDKs, libraries and Win32 calls. Wine has to emulate(!) all of this in order to achieve a godd gaming experience. In virtualization technology, for games, developers only need to worry about hardware acceleration. In theory it's much more simpler than what Wine developers have to do hence it has more probability to work.

If it was that simple, why does it take so much time to introduce this feature? It's been in Vmware for a long time, but even a 2d game I tried there was unplayable. And VirtualBox has Sun resources behind it, which wine doesn't have.

Wine translates DirectX calls into OpenGl calls. If the game is opengl in the first place, a huge amount of translation and possible bugs is eliminated.

---

### Post by mips on 2008-12-19
> **cb951303 said:**
> In their site they state that they are also planning D3D acceleration. YAY!!


DirectX support would be great. Counter Strike Source simply does not work for me in wine and I would gladly run it in a VM if the DirectX support is available.

---

### Post by grazed on 2008-12-19
does anyone know if this release fixed the bug with seamless mode and compiz?

---

### Post by cb951303 on 2008-12-19
> **SupaSonic said:**
> If it was that simple, why does it take so much time to introduce this feature? It's been in Vmware for a long time, but even a 2d game I tried there was unplayable. And VirtualBox has Sun resources behind it, which wine doesn't have.

because none of the graphic card manufacturers releases their specs!!!

> 
Wine translates DirectX calls into OpenGl calls. If the game is opengl in the first place, a huge amount of translation and possible bugs is eliminated.

I totally agree with you but you disregard a simple fact that I explained to you earlier. Games consists of several libraries and most importantly Win32 specific code. Unless wine manages to emulate all of this there will always be games that you can't play. In my experiences (and I tried a *lots* of game till I gave up) the games that work acceptably in wine are not too many including OpenGL ones.

---

