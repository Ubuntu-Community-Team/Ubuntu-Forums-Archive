---
title: "Help with Setting up Office / Clinic Network"
date: 2010-08-02
forum: Server Platforms
---

### Post by Aidenairel on 2010-08-02
I didn't know where else to post this, as I have also posted this in the Networkign ssection, but figured I might get more responses here. :) So please humour this n00b.

Ok guys, here's the deal.

I need to set up an office network with limited Internet connectivity,  but with data access across all clients in the network with a central  data server.

Basically, there will be 4 Client PCs, 1 data server with information on  it, and the preferred method of tying this all together would be WiFi,  since laying cables would be out of the question (it's a dental clinic).

The idea is that patient data would be modifiable from all clients, on  the data server, but with some semblance of security locked in to ensure  data is not tampered with willy-nilly. Internet access should also be  available to all client PCs.

What do I go with here? Standard desktop installations on the 4 clients,  and 1 server installation? What about security? Clinic management  software for Linux? Any ideas anyone? I don't want to have to resort to  using Windows as the platform, as the licensing fees are not exactly  palatable, and we're running on a tight budget here. (All of this has to  be up and running for less than $2500).

Don't get me started on Apache, etc, because I am indeed quite lost on those topics.

I hope this is the right place, as I am a bit lost wondering how to get this up and running.

Cheers.

---

### Post by Vincentlaborant on 2010-08-02
I would use a powerline network connection if possible. A powerline connection basically is a wired network connection to the electrical network via a outlet on the wall. My dentist has that, since all the computers are in corners of the office.

This gives good networking speed as well as the fact that you do not have interference with machines that might not function properly due to wifi signals.

You describe you need 4 clients and 1 server, in which the server has all the data. If the data has to be accessible from all the clients, I would recommend storing your data in a shared folder.

I would put all the software on the server, and let the clients do a networkboot. This means that you can control the rights of the clients via the server. You can give rights to maintain the server/ clients, read/ write acces to folders and more.

I hope this will get you started. If you have more specific questions, I can always try to give you the answers you need.

---

### Post by Aidenairel on 2010-08-02
Hi Vincent, thanks for the quick reply!

Ok, I read elsewhere on these forums and on the Internet that since it is a small office environment, I would not need to run Ubuntu Server, and that I could get away with just using Ubuntu Desktop, with Server packages downloaded and configured properly. Would that be accurate? I see that USE is CLI, and I do not fancy having to do everything through command line jargon. A GUI would be best.

Also, when you say networkboot, what exactly do you mean? How does that actually work?

---

### Post by ahbart on 2010-08-02
> **Aidenairel said:**
> Also, when you say networkboot, what exactly do you mean? How does that actually work?
Have a look here: [LTSP]("https://help.ubuntu.com/community/UbuntuLTSP")

---

### Post by mcarrara on 2010-08-02
to me there are several issues that have mutually exclusive answers.
1. Network hardware
2. Network operating system
3. Security
4. Applications.

Before you decide on an infrastructure you better make sure that the applications you NEED to run can work on your proposed system.  I would determine the clinic management software first.  To a  dentist, dental clinic software is a huge market, it is not.  I would imagine there are very few providers of turnkey software.  Could there be an open source project?  Sure but I doubt it is easy to deploy.  I would bet you will need to run a Windows client on the desktops.  Depending on how the software is configured you may or may not be able to run Linux on the server.  It would be a waste of valuable resources (time and money) to set up the perfect Linux based system only to find our no software that you need to use runs on it.

---

### Post by Aidenairel on 2010-08-02
Thanks for the responses, guys.

Ok, the LTSP link seems quite useful, and I shall delve into it further when I can, so thanks ahbart!

Mcarrara : Its a private practise with relatively low volume, so a dedicated management software would be overkill, methinks. I wonder if going with a folder sharing concept as explained by Vincent earlier, would be the way to go, since it would then be possible to set the access limits for the client PCs?

---

### Post by mcarrara on 2010-08-02
My only concern would be with HIPPA compliance.  Security must be air tight.  I would make sure you had a good password policy in place and stick to it.  That all said yes a shared folder would seem to work.  Wireless is possible, again make sure you have good security.  I have not looked at LTSP is a few years so I can't say much about that but it would be a (relatively) simple thing to set up with Ubuntu.

Mark

---

### Post by Aidenairel on 2010-08-02
Security is an understandable concern, and all employees have signed NDAs as part of their employment contracts. :)

Ok, hardware-wise, there will be 4 fully fledged PCs acting as the clients, and the server will be a normal PC with more RAM, a bigger HDD and a faster processor.

How do I go about setting this up?

Can I just use a standard desktop distro like Ubuntu for all 5 machines, and just install and configure the relevant server/network packages?

---

### Post by mcarrara on 2010-08-03
I understand your reluctance to use a server, you grew up using a GUI, but the overhead of the GUI wll effect performance.  I prefer to use Webmin to mange my servers, GUI like and out overhead.  I use Putty for simple tasks where the command line is not that hard.

I would set up the 4 clients identically and make sure they work stand alone.  Set up the server as a server then if you really must install the desktop GUI.  When installing the server you shouldn't need Samba because this will be an all Linux system, if you need printing install CUPS.

Now you will need to learn how to put everything together.  My FAVORITE resource is a book, yes an old fashion real dead tree book.  "Linux Administration Handbook" by Evi Nemeth, Garth Snyder and Trent Hein.  Mine is always on my desk within easy reach.  I refer to it every week.

Of course there is the Internet and this forum, but I really think that book will make your job a whole lot easier.

I hope this all helps.

Mark

---

### Post by gordintoronto on 2010-08-03
You have ignored the most important advice you have received: look at the application software before you even think about hardware, networks and operating systems. Have you talked to other dentists about what they use? Have you looked at demos at dental conventions? Examined the ads in trade publications?

One package available for Linux is called Openmolar. It would be easy to have a look at what it can do.

Oh, one other thing: if your budget is supposed to cover everything, it's not realistic. The day will come when you must buy some professional help, so add a grand just for that.

---

### Post by Aidenairel on 2010-08-04
Mcarrara : Thanks mate, that helps a lot. I shall go book hunting this weekend, and I shall be making the decisions for hardware by the end of the week, as I am headed off on a business trip.

Gordin : I have heard of that, and will take a closer look at it, thanks to your prompting.

The budget is there because it is the one given to me. The problem with the situation I have is that this is Malaysia, and commercial software for this sort of application costs around 3 to 4 thousand US dollars alone, without set up and tech support. I know this, because the person I'm helping with this, is a former president of the Malaysian Association of Orthodontists, and knows her stuff.

Windows licenses here are through the roof, ever since the government decided to get into bed with Microsoft, so it is just not a viable option financially.

---

