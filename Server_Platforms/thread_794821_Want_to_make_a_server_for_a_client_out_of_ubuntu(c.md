---
title: "Want to make a server for a client out of ubuntu(clients use mac and pc)"
date: 2008-05-15
forum: Server Platforms
---

### Post by DJSchmidty on 2008-05-15
K, so me and my partner do IT support for several clients, this one in particular is having a HUGE problem with their windows small business server 2003.  Part of which is because its a hacked bootleg version.  I've been telling him about my addiction to ubuntu, and how it can be run as a server n stuff, and he wants to hear more about it.  Heres what this particular client needs:

The server computer controls the DHCP, they have a wireless router as well, but thats just for the laptops when they are outside (I believe its a wrt54g linksys)  ANyway, the server now runs the dchp, and the dns, it also does the most important thing the business owner wants -Back Up-

Because most of the computers are macs, and maybe a few PCs, I don't know if its possible to run a xubuntu OS with the capabilities of what I and they need.  I'm kinda new to ubuntu, but I have it on all my machines (2 laptops, and 4 computers) I even made my dad switch over, and hes pissed cause all he does is go on aol, lololol.

So, what are some recommended programs that are easy to configure for this, and am I thinking right in loading on xubuntu (because its a stripped down version of the gnome interface) and installing a program for dchp, dns, and backup?

Any help would be great, I can't believe I never heard or used this OS before, i'm absolutely addicted to ubuntu, and would never go back to windows again if it werent that I also do some flash animation on the side for websites...

Thanx in advance!!:popcorn:

---

### Post by cdtech on 2008-05-15
Here's the new [[COLOR="DarkRed"]Hardy server[/COLOR]]("http://howtoforge.com/perfect-server-ubuntu8.04-lts") setup guide. For backup, it's as simple as a script (using a backup medium) or more complex such as running a raid setup (with an extra drive).

Hope this helps....

PS.
> I'm kinda new to ubuntu, but I have it on all my machines (2 laptops, and 4 computers)
> I can't believe I never heard or used this OS before
Do what?

---

### Post by DJSchmidty on 2008-05-15
wow thanx for the quick reply, that seems like alot of instructions.  I was hoping for a GUI of some sort though, thats why I wanted to use Xubuntu, because its lite-weight.  Is it hightly recommended to use the server edition of ubuntu? i'm really not to up to snuff on the terminal commands, and if something happens after I set it up, i'll be SOL cause I won't know waht to do.  If there was a GUI, atleast I could thumb through some menus and figure it out....

(Not sure what your asking 'do what')

---

### Post by Frem on 2008-05-15
Not to rain on your party, but you should really understand a product before rolling it out to customers. GUIs can't do everything, and that tutorial is fairly streightforward.

In addition, if something does break, the experiance of setting it up manually will be a lot more valuable for fixing it than if you'd used a GUI.

All this being said, Googling for "Webmin" may turn up something useful to you. ;-)

---

### Post by DJSchmidty on 2008-05-15
Oh, I completely agree.  I have a dummy computer setup right now, and i'm just putting different verions of ubuntu and seeing exactly what I can do with each one of them (I'm saving server for last....)

I will probably make that tutorial my mission for tomorrow night, to see what I can do If I can get it to work in my home first, then run some real world scenarios, and try to cram as much as I can about the terminal.

I'm hooked, i aint leavin anytime soon, I just wanted to see if there was a visually pleasing version of what I kinda knew already was gonna be a pita to learn....

I have looked into webmin before, have it running right now on a xubuntu install on that test computer, seems to have quite the array of options!!!  BTW, that tutorial I noticed didn't have anything about the server controlling the dhcp (or maybe I didn't read it enough) only got to page 3, then I said i'll read it later when I actually install ubuntu server......

---

### Post by hyper_ch on 2008-05-15
(1) that hardy setup guide aims at installing a webserver and associated services... I don't think that's what you're looking for.

(2) As I understand it you want the server to do two things:
- act as dhcp server
- act as backup server for company data

Is that right?

---

### Post by DJSchmidty on 2008-05-15
pretty much.  also a dns, and its gotta work with both macs and pcs...

---

### Post by cdtech on 2008-05-15
> Want to make a **server** for a client out of ubuntu

That is a guide to setup the "The Perfect Server" using Ubuntu. You don't have to install everything. Learn the command line; it will be valuable to you in the long run. Everything you install on your server, learn to do it by the command line and be sure to keep a journal on your procedures.

It is frustrating to forget what, or how you did something. I keep a notebook as well as a blog, listing all of my procedures that I used on my server. 

Always remember to backup your work when you’re satisfied with the way it performs. I backup using a 4GB USB pen drive, which also holds all of my web server files (something you may want to keep in mind, (the server version is lightweight)).

Just some advice….

---

### Post by hyper_ch on 2008-05-15
well, for DHCP there are many howtos around (never tried any of those):

[http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/dchp.htm](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/dchp.htm)
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
[http://www.linux.org/docs/ldp/howto/DHCP/index.html](http://www.linux.org/docs/ldp/howto/DHCP/index.html)

--> [http://www.google.com/search?hl=en&q=howto+linux+dhcp&btnG=Google-Suche&meta=](http://www.google.com/search?hl=en&q=howto+linux+dhcp&btnG=Google-Suche&meta=)


And as for the backup... I love rsync to do backups. Mac should be able to use rsync (somehow) and on windows I used cygwin to setup a rsync server....

Another option would be, if the server would directly act as file server... meaning that the clients store their documents on the server...

---

### Post by cdtech on 2008-05-15
> And as for the backup... I love rsync to do backups. Mac should be able to use rsync (somehow) and on windows I used cygwin to setup a rsync server....

For a company, you'll want to run a file server for all of the workstations so the backup would be of the server only, right? All of the workstations can have their own individual backup scheme. What backup method are they using now?

You could use a tape backup or a secondary hard drive along with tar or rsync respectively, or even run a dual-node cluster configuration setup running Heartbeat (if you want to really get into it).

The configurations are endless, you have to know what you expect out of your server before you begin.

---

### Post by Mr_Whippy on 2008-05-15
To the OP,

I have been looking for a lot of documentation on setting up servers, and full networks using ubuntu server, and i stumbled across these earlier today not sure if they are helpfull yet, but they look it to me,

[https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by DJSchmidty on 2008-05-15
Ok, so how its set up now. The guy that set the network up for them made it so each computer backs up their work (a particular folder, or multiple folders) to either an active directory, or some sort of locally shared folder on the server.  I know that sitting at one of the macs, I can go into the server under his login name and view everything that has been backed up.  On the server itself, is a tape drive (Which is giving alot of problems cause they are storing 33 gigs of data on 35 gig tapes)  But this whole setup is crashing down.  The server died last week, and my partner is scrambling to get it back up and running.  For now, they are passing around the tape drive to each computer and backing it up that way...

I told him that I think it would be fine just to back it up to a 500gb external (Do they make a raid external drive?)  Anywho, so thats pretty much the most important thing is having a server that will store the backups from all the client computers (both mac n pc).  I'm just messin around with xunbuntu and its damn fast on my 4 year old machine, i know you guys are gonna yell at me, but I think I would want to find a solution using a GUI (Not just for me not knowing 90% of the terminal commands, but more because most of our clients are finicky, if you tell them linux and they don't under stand, they FREAK OUT.  This way if they wanted to just move the mouse around and take a look around the OS, they can.)

I'm gonna read all of the links you guys provided tonight, thanx for all the replys so far!!

---

### Post by hyper_ch on 2008-05-15
well, I just think it might be better if all clients will auto-save their documents on the server...
but then you'll also need a backup there....

---

### Post by DJSchmidty on 2008-05-15
yea, exactly....  Like, i'd like the clients documents to autosave to the server after say, 9 o clock, and then when thats done, i'd like the server to back up to a tape drive, or some sort of external drive say at like 5 am or even 9 am, this way the server is doing what its gotta do when the workers are going back to their designing and stuff...

---

