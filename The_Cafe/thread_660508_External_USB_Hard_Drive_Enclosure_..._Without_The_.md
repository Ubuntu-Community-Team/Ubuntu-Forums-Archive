---
title: "External USB Hard Drive Enclosure ... Without The Enclosure"
date: 2008-01-06
forum: The Cafe
---

### Post by Atreus12 on 2008-01-06
I've got a router with 2 usb ports on it, running dd-wrt. I've also got a few IDE hard drives laying around ... I bet you can see where this is going.

I was looking at the external hard drive enclosures, but they seem to be poorly designed / built and don't last very long. A lot of the complaints are overheating.

Is there a way to do this without the enclosure (avoiding the overheating problem)? All I really need is a little unit that goes from IDE to USB, and some way to power the drive. Sealing the drive in a closed box seems kind of pointless to me.

Anyone attempt this and/or have suggestions?

---

### Post by bill_greene on 2008-01-06
This is what I use.

[http://www.geeks.com/details.asp?invtid=USB2IDE-N&cat=CBL]("http://www.geeks.com/details.asp?invtid=USB2IDE-N&cat=CBL")

---

### Post by Lostincyberspace on 2008-01-06
I saw them one time at pcclub computers but they are kind of hard to find.

---

### Post by kevdog on 2008-01-06
I see what you want to do, however can you be more specific about what function you want those hard drives to serve and how you are setting up dd-wrt to make use of that space? JFS?

---

### Post by D-EJ915 on 2008-01-06
I'll post a pic of the setup I have going on with mine, basically I just have a fan hooked up and blowing over my 2 drives ( have gaps in between them and the desk underneath) and it keeps them much, much cooler than without the fan.  I stole that cage from an old antec case I am not using but you can use anything, in front of that setup you can just see my laptop which is sitting on a shoe box I converted into a fan holder and that is cooling it (also propped up))

[IMG]http://img.photobucket.com/albums/v104/enthauptet/bin/external_ghettojob.jpg[/IMG]

---

### Post by mips on 2008-01-07
It sounds like you want to create a NAS device maybe? Is this possible with your router & dd-wrt?

You do get bigger, more ventilated external enclosures with small fans. Seems like a neater, tidier solution to me.

---

### Post by popch on 2008-01-07
The USB2 to IDE cable would do the trick. 

So would an enclosure with the case (enclosing box) left out.

I have been using external USB disks with enclosures for years and am still waiting for one to burn out. Enclosures work for me jut fine and are a bit easier to dust off.

If you're really cheap use the case and power supply of an old PC

---

### Post by Atreus12 on 2008-01-08
> **mips said:**
> It sounds like you want to create a NAS device maybe? Is this possible with your router & dd-wrt?

You do get bigger, more ventilated external enclosures with small fans. Seems like a neater, tidier solution to me.

I think it is possible. I know I can load open-wrt packages on the router, and already have a usb thumb drive connected acting as expanded hard drive space for the router. I have ext3 support, and I plan to share the drive on the network (maybe samba, I haven't decided), and configure a bittorrent client to run on the router and watch a folder on the shard drive for torrent files, and then automatically download them. That way I can easily download linux distributions without having to leave my computer on all the time.

Maybe I could have my email client automatically put torrent attachments in that folder, so that I could easily initiate downloads from anywhere. I guess I don't know 100% what I'm going to do with it, but the possibilities are intriguing. It just seemed like something cool I could do inexpensively.

I realize that "good quality" external enclosures are available, but I would like to do this cheaply. Maybe my efforts would be better spent putting together a server and forgetting the whole router thing?


> **bill_greene said:**
> This is what I use.

[http://www.geeks.com/details.asp?invtid=USB2IDE-N&cat=CBL]("http://www.geeks.com/details.asp?invtid=USB2IDE-N&cat=CBL")


do those cables require any special drivers beyond typical usb support?

> **D-EJ915 said:**
> I'll post a pic of the setup I have going on with mine, basically I just have a fan hooked up and blowing over my 2 drives ( have gaps in between them and the desk underneath) and it keeps them much, much cooler than without the fan.  I stole that cage from an old antec case I am not using but you can use anything, in front of that setup you can just see my laptop which is sitting on a shoe box I converted into a fan holder and that is cooling it (also propped up))


Could you be more specific on the connections you are using? Are you using the drive as a usb drive?

---

### Post by mips on 2008-01-09
I actually saw a nice small (20 cigarette pack size) IDE/SATA to usb converter in the pc shop yesterday when I went to go buy some ram.

---

