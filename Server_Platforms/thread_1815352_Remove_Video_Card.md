---
title: "Remove Video Card"
date: 2011-07-31
forum: Server Platforms
---

### Post by expatCM on 2011-07-31
I would like to remove the video card on my server since having it there accomplishes nothing.   If I simply take it out the system will not boot.

I took a look in the bios settings and I see nothing relating to any video card but I do see a setting where you can enable Headless Mode.  I took a look on google and this apparently relates to access where there is no need for a keyboard or mouse.

How do people set their systems so that you can remove the video card and still get the system to boot?

---

### Post by CharlesA on 2011-07-31
Not a clue. I have a video card in my server (which runs headless) so I can actually get console access if I need to - if it fails to boot, for example.

---

### Post by expatCM on 2011-07-31
I have found that when the video card fails it stops the server so it is perhaps a good idea to remove the card.  It can be done but the need is how.

---

### Post by CharlesA on 2011-08-01
> **expatCM said:**
> I have found that when the video card fails it stops the server so it is perhaps a good idea to remove the card.  It can be done but the need is how.

I don't know of any machine that will run without a video card of some sort - most won't even POST.

If the card goes out, just replace it.

---

### Post by expatCM on 2011-08-01
seems like waste of a card ....  I mean you install it and do not use it and then have to replace it when it fails....  but it serves no purpose (apart from the one time in a blue moon when the server will not boot and you have to work out why).

---

### Post by Wim Sturkenboom on 2011-08-01
You might have a setting in the BIOS called something like "halt on". If so, it might have an option to ignore all errors. Usual options are 'halt on all errors' and 'halt on all errors but keyboard'

I have a Phoenix BIOS that can ignore all errors; funny enough it's called 'halt on no errors' ;) Not tried to remove my videocard, by the way.

However, Linux might not be too happy if it can't configure a videocard. So that might be the next hurdle.

---

### Post by Entilza on 2011-08-03
This is why server boards come with onboard graphic cards on the motherboard.

The new intel procesors have integrated video on the chip but you need a motherboard that can support thiat.

Your system wont boot without a graphics card give up on that idea :)  Get a cheap graphics cards and put it in there.

---

### Post by bakegoodz on 2011-08-04
All the BIOS I'm aware of are coded to always need a video device. A server can use an old or very low end video card. I remember a couple years ago hearing about a serial terminal video card, don't remember the manufacture or model. I think that would be really cool server video card. One could remote access the BIOS.

---

### Post by WhiteHorse on 2011-08-04
Are you some kind of video-card-ist?
Try this:
In your bios, change the setting to emulate video card. If that doesn't work, solder some wires onto the motherboard to trick it into thinking there's a video card.

---

### Post by giraid on 2011-08-14
I'm in a similar situation, except I know my box will boot without a video card. It's a WHS box came w/o a video card. It ran WHS and windows server 2008 without a video card just fine. But when I remove the video card after installing ubuntu I cant connect to it via tight VNC anymore. I think Ubuntu checks for hardware at start up or something like that. Is there a way to stop the OS from doing that?

---

### Post by scorp123 on 2011-08-15
> **expatCM said:**
> If I simply take it out the system will not boot. Welcome to 1981 and the wonderful world of PC's. Your server is an Intel or AMD machine? Congrats. It works as designed ... in 1981.

Most PC-based hardware until this very day have a BIOS (Basic Input/Output System). And the BIOS dictates that there be three things present or else it will refuse to boot:

- a CPU
- RAM chips
- a graphics chip

Remove any of those components and the PC in question will only beep. Maybe not even that. But it definitely will not boot.

There may be some newer server-grade motherboards that can indeed do without a graphics card but these tend to be non-Intel/non-AMD CPU designs and/or they don't have a BIOS (e.g. they use EFI instead) and/or they're very expensive and hard to get (e.g. you'd have to buy a dedicated server machine e.g. from Oracle or HP to get your hands on one of those).

As soon as you use PC-based hardware with a BIOS = graphics card is a "must have". The only thing you could do in such a case is to use a super cheap low-spec graphics card.

---

### Post by expatCM on 2011-08-15
...  and the setting in Bios, select to enable 'headless server' seems like wasted space.  What does it do you may wonder.  Me too.

The retirement of traditional Bios is well overdue.  The quality of the Bios user manual is the same quality as the Bios.  Perhaps I appear a little harsh?  Try compare the manual with the Bios settings (any version) and see what you find.

---

### Post by scorp123 on 2011-08-15
> **expatCM said:**
> ...  and the setting in Bios, select to enable 'headless server' seems like wasted space. Some newer machines that really are server-grade have that, yes. If that option is there ... by all means: use it.

But you know: people tend to call a simple home-PC a *"server"* just because there's now a web page running on it. So that's not the kind of machine you're talking about. Such hardware --no matter in what role it is used-- is still pretty much 1981 technology with all its limitations. And I bet that most non-IT-professionals on this very forum tend to have this type of hardware (e.g. you can't run it without VGA card) and not the modern server-type hardware that could easily do it.

> **expatCM said:**
>  The retirement of traditional Bios is well overdue.  Totally! Many things in there just make no sense at all in our time.

---

### Post by giraid on 2011-08-15
> **scorp123 said:**
> Welcome to 1981 and the wonderful world of PC's. Your server is an Intel or AMD machine? Congrats. It works as designed ... in 1981.

Most PC-based hardware until this very day have a BIOS (Basic Input/Output System). And the BIOS dictates that there be three things present or else it will refuse to boot:

- a CPU
- RAM chips
- a graphics chip

Remove any of those components and the PC in question will only beep. Maybe not even that. But it definitely will not boot.

There may be some newer server-grade motherboards that can indeed do without a graphics card but these tend to be non-Intel/non-AMD CPU designs and/or they don't have a BIOS (e.g. they use EFI instead) and/or they're very expensive and hard to get (e.g. you'd have to buy a dedicated server machine e.g. from Oracle or HP to get your hands on one of those).

As soon as you use PC-based hardware with a BIOS = graphics card is a "must have". The only thing you could do in such a case is to use a super cheap low-spec graphics card.

I don't think it is true that no PC with bios can without a video card. my [ss4200]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859117003") runs perfectly fine without a video card. In fact, I think most of the windows Home Servers on the market run without video cards, and I'm pretty sure they don't have server grade hardware with their sub $500 price tags. I think there is a way for the motherboard manufacture to stop the bios from force checking on hardware.

---

### Post by CharlesA on 2011-08-15
> **giraid said:**
> I don't think it is true that no PC with bios can without a video card. my [ss4200]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859117003") runs perfectly fine without a video card. In fact, I think most of the windows Home Servers on the market run without video cards, and I'm pretty sure they don't have server grade hardware with their sub $500 price tags. I think there is a way for the motherboard manufacture to stop the bios from force checking on hardware.

Those are special, in that case, since they are built to be accessed via web interface and not from the "console"

---

