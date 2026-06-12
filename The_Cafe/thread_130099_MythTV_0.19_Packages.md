---
title: "MythTV 0.19 Packages"
date: 2006-02-15
forum: The Cafe
---

### Post by ORiON2012 on 2006-02-15
Dapper's out, as posted on my blog and the repo frontpage, these packages are now gone.

---

### Post by ORiON2012 on 2006-02-15
Forgot to stress that these packages should be considered unstable. There's been around 4GB worth transfered since the I posted the mythtv-users and only 6-7 people that have reported problems, but that's not nearly enough to claim that you can upgrade care free :)

---

### Post by nikopol on 2006-02-15
4 Gb! Wow - hope your link is holding up...

I've reported a problem with mythweb in the Dapper thread. Anyone else experiencing it under Breezy?

---

### Post by joflow on 2006-02-15
I wished my tuner worked with Linux...always wanted to try MythTV.  Damn you, ATI.

Good job on the deb though.  Hope I can use it in the future.

---

### Post by mikedtemple on 2006-02-16
Only a minor problem with mythweb here, but if you follow the instructions in the mythweb README file, you're ok to go.  Thanks for the build.  Packages are great- and I'm actually noticing a much FASTER channel change.

---

### Post by nikopol on 2006-02-20
I've fiddled about with MythWeb but I think the fundamental problem for me (under Dapper) is that it seems to be problematic downgrading from php5 to 4. I think that php4 doesn't fully install or apache isn't really compatible with it. So I guess mythweb won't work under Dapper for the time being.

---

### Post by ORiON2012 on 2006-02-20
I fixed the dependencies a while ago, php4 or 5 will satisfy the mythweb dependencies. I have mythweb working on php5 in Breezy, do you need php4 for some other reason?

---

### Post by nikopol on 2006-02-20
I thought MythWeb was dependent on php4? my bad - will have another look at what is the problem in Dapper and post back

---

### Post by TechSonic on 2006-02-20
What is this?

---

### Post by fubarbundy on 2006-02-27
[QUOTE=ORiON2012]I've posted this on the MythTV user's mailinglist, thought I'd put it here too. 

I've created some packages for Ubuntu. They were created
for Breezy, but from my initial tests, at least mythfrontend also works
on Dapper. There are issues on Dapper with naming for plugins like 
mythbrowser and the KDE libs it requires.
Please back up your database before installing them.

[http://deb.thehunter.ws/dists/breezy/mythtv-stable/](http://deb.thehunter.ws/dists/breezy/mythtv-stable/)
Detailed information about how they're compiled can be found at
[http://www.thehunter.ws/repo/packages/breezy](http://www.thehunter.ws/repo/packages/breezy) , scroll down to
"mythtv-stable".

I would greatly appreciate it if people would post any problems they run into so I can fix them as quickly as possible.[/QUOTE]

Packages seem to be working fine on my machine after a couple of weeks. I have run into two problems, but I suspect they're upstream as I've read about them elsewhere (I'm using 2 DVB-T digital tuners):

1. Massively increased CPU usage on both backend and frontend compared to 0.18.1
2. When initially tuning to any channel (or using a tuner for the first time?) it takes longer than 0.18.1 to tune in, and then the video will alternate between a second or so played back too fast, and then a second or so played back in slow mo (giving a sort of jerky effect). Audio is fine. The workaround for me at the moment is to increase playback speed (3x or 5x) until myth hits the end of the buffer and jumps back to normal speed playback.

I can confirm that for me the problems with mythweb were fixed with a bit of tinkering with mod-rewrite, overrides and php debs, as discussed here: [http://ubuntuforums.org/showthread.php?t=128748](http://ubuntuforums.org/showthread.php?t=128748). The only thing I can suggest is maybe making sure the right php and apache packages are required for mythweb??

Thanks for all the hard work :)

---

### Post by evenstranger on 2006-03-25
I have had similar problems configuring mythweb but nothing to bad. 

My major problem with the upgrade has been with livetv as soon as I change the channel once it loses all keyboard input and I have to kill mythfrontend to get out of it. Have tried getting focus back to the window and also tried using the telnet interface which works up to the same point as soon as the channel is changed it still allows me to send keys but there is no response from the app.

Other than that all seems to be working well. Thanks for the packages.

---

### Post by sdyson on 2006-04-28
[QUOTE=evenstranger]
My major problem with the upgrade has been with livetv as soon as I change the channel once it loses all keyboard input and I have to kill mythfrontend to get out of it. Have tried getting focus back to the window and also tried using the telnet interface which works up to the same point as soon as the channel is changed it still allows me to send keys but there is no response from the app.

Other than that all seems to be working well. Thanks for the packages.[/QUOTE]

I'm just setting up a myth box and have experienced this same problem. It doesn't happen every time but is rendering the box pretty useless. Did you find a cause or solution?

---

### Post by michaelnix on 2006-05-02
I followed the instructions given on the webpage linked to by the thread starter.  

However, when I choose MythTv in Adept it says it will break the install.  Has anyone else had this problem.

I am using Kubuntu 5.10

---

### Post by badalf33 on 2006-06-15
Hello,

What's wrong with the repository ??? Is it down ????

---

### Post by awakatanka on 2006-06-15
Only problem i have is that probably my driver is chrashing (much) if i change a channel. That is if i use it on the backend machine but also on a remote machine. And i have to reboot the backend server machine.

Got a haugepage pvr-500.

But mythtv is getting better and better.

Ps. also another thing i noticed the quality of the channels is a bit worse in mythtv then in windows xp. It has more (how you call it) snow in the picture, under windows i have a perfect channel.

---

### Post by badalf33 on 2006-06-21
[QUOTE=ORiON2012]Dapper's out, as posted on my blog and the repo frontpage, these packages are now gone.[/QUOTE]

Hello,
What is the address of the repo frontpage please ?????


Thanks a lot for your hard work .....

---

### Post by ORiON2012 on 2006-06-21
[QUOTE=badalf33]Hello,
What is the address of the repo frontpage please ?????
[/QUOTE]
Sorry if I've caused confusion. I no longer have a repo. The packages are *gone* and I no longer use Ubuntu, try marillat's or perhaps ask on the mythtv-users mailing list if you don't care to compile myth from source.

---

### Post by badalf33 on 2006-06-21
OK thank you for your answer ....

Where can I download your breezy package ?

Good luck with Gentoo.

---

### Post by badalf33 on 2006-06-22
Up !!!!!!!!

---

