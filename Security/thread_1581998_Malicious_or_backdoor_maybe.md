---
title: "Malicious or backdoor maybe??"
date: 2010-09-25
forum: Security
---

### Post by Codecaine_21 on 2010-09-25
i installed a fresh copy of ubuntu  10.04 and during the installation i opted to update my security updates  myself but everytime i start my computer up an automatic security update comes up  even though i opted to update myself. and it wants to update api  packages for perl and install ssh servers... looks as to it might be a backdoor  or something malicious!! i opened  up firestarter and my ip was calling  services that i was not calling like i uninstalled ssh server and my ip  was making calls to it but i wasnt running the server and it showed up  in red i guess because its uninstalled. but i will recieve denial of  service updates and if i leave my computer on over night the computer is  on and running but my screen is detached. like the computer is on but  the screen is off even though i have all the wires plugged in. The  monitor works again if i restart my computer. i opened up my routers  server page for netgear and seen a few different ip's attached but when i  used nmap and fping it came back that they were not alive or the word  used was "Unreachable" any insight??

---

### Post by mrhhug on 2010-09-25
hmm, do you use strong password and WPA2 encription on your router? and a strong password for all your users on this computer?

this is a fresh install of ubuntu? you did a md5 sum on the iso before you installed right? 

seems like it might be a funky load or possibly like you think someone has taken control of your system

i would check hardware too fitness tests and memtests. here is what i would do if you were paying me to diagnose this problem.

1)make sure router has WPA and strong password
2)run a fitness test
3)run a memtest
4)check the iso that you used to install ubuntu with md5sum

reasses the situation

---

### Post by Codecaine_21 on 2010-09-25
i wiped everything because this was a problem before!! so i did a fresh install quite a few times!! and everytime it comes back!! i think the updates are being requested from my computer once i start an instance of firefox!! When i start firefox thats when the updates come and then the traffic from my ip when i am not doing anything but coding on code::blocks. i uninstalled the ssh server!! my passwords are tight mem is good!! and i did the md5 check!!

---

### Post by mrhhug on 2010-09-25
> an automatic security update comes up even though i opted to update myself.

can you be more specific on this screenshots are great

> and install ssh servers

whats asking to install this server?

> recieve denial of service updates 

what gave you this error?

how old is your hard drive / motherboard?

---

### Post by Codecaine_21 on 2010-09-25
well when i install my 32bit ubuntu 10.04 server edition it asks me if i want to manage updates my self or make that task automatic. i chose manual this time and automatic updates are still coming thru. they are packages that ask permission to download. like ssh server or perl api socket libraries looks like malicious stuff!! but i restarted the comp and no update manager came so no screen shot for jnow but i did manage to grab a screen shot of an error message saying that my iphone could not be mounted because it is already mounted. The automatic security update manager is asking to install the ssh server. and i again i said that i would manually manage! and the denial of service came as an automatic update package was denial of service and everything would stop working till i rebooted. and the drive isnt that old i dont know how to uplaod attachments on this site either

---

### Post by Ryan Dwyer on 2010-09-25
I see nothing wrong here.

You opted to install the updates yourself, and it's notifying you that there are updates available. It's not installing them for you. The traffic you see is probably this.

Ubuntu has an SSH client installed by default, so you can expect to see updates for it. The application "ssh" is not an SSH server.

The monitor turns off after a period of inactivity to save power.

---

### Post by Codecaine_21 on 2010-09-25
the monitor doesnt hibernate or sleep im not slow and definitely not a noob to programming, linux, or computers! i have been using ubuntu for almost 2 years i have used windows and mac and have never seen a monitor detach from the pc! it doesnt just sleep like if i move the mouse it will turn back on no the monitor will completely detach and the only way to get it working again is restart my comp! and when my monitor is detached it also unmounts my iphone so if i leave my iphone charging over night when the monitor detaches or whatever is going on so does my iphone! it stops charging like i dont even have it plugged in at all?? but the the traffic is my ip address calling port 80 port 443 port 22 and you are saying these calls to these services are cool and should be there? idk man i have been with linux for awhile and all this has never happened before it is not normal! i have never had a problem with the monitor or all this bullcrap before so this is y im am curious as to what is going on!!

---

### Post by mrhhug on 2010-09-25
> **Codecaine_21 said:**
> the monitor doesnt hibernate or sleep im not slow and definitely not a noob to programming, linux, or computers! i have been using ubuntu for almost 2 years i have used windows and mac and have never seen a monitor detach from the pc! it doesnt just sleep like if i move the mouse it will turn back on no the monitor will completely detach and the only way to get it working again is restart my comp! and when my monitor is detached it also unmounts my iphone so if i leave my iphone charging over night when the monitor detaches or whatever is going on so does my iphone! it stops charging like i dont even have it plugged in at all?? but the the traffic is my ip address calling port 80 port 443 port 22 and you are saying these calls to these services are cool and should be there? idk man i have been with linux for awhile and all this has never happened before it is not normal! i have never had a problem with the monitor or all this bullcrap before so this is y im am curious as to what is going on!!

make sure you graphics drivers are current

---

### Post by CharlesA on 2010-09-25
Question, are you seeing something like this:

```

5 packages can be updated.
5 updates are security updates.

```

---

### Post by OpSecShellshock on 2010-09-26
> **Codecaine_21 said:**
> the monitor doesnt hibernate or sleep im not slow and definitely not a noob to programming, linux, or computers! i have been using ubuntu for almost 2 years i have used windows and mac and have never seen a monitor detach from the pc! it doesnt just sleep like if i move the mouse it will turn back on no the monitor will completely detach and the only way to get it working again is restart my comp! and when my monitor is detached it also unmounts my iphone so if i leave my iphone charging over night when the monitor detaches or whatever is going on so does my iphone! it stops charging like i dont even have it plugged in at all?? but the the traffic is my ip address calling port 80 port 443 port 22 and you are saying these calls to these services are cool and should be there? idk man i have been with linux for awhile and all this has never happened before it is not normal! i have never had a problem with the monitor or all this bullcrap before so this is y im am curious as to what is going on!!

The hardware activity sounds like one of the power saving features that tend to be enabled on newer off-the-shelf computers. That would be configured in the BIOS, not in the OS. After a certain amount of idle time, the current state will be saved in memory (like the hibernation feature of the OS), and the networking and attached devices will also be disabled, the hard drive will spin down, and to all appearances the computer will look as though it's been shut down. Since all attached devices are affected, the computer can't be brought out of this state by moving the mouse or typing on the keyboard. Usually it requires pressing the power button. To turn off this feature, you'd need to access the BIOS at boot (usually by hitting F2, I think) and navigate the interface until you get to a power saving menu.

---

### Post by mrhhug on 2010-09-26
> **OpSecShellshock said:**
> The hardware activity sounds like one of the power saving features that tend to be enabled on newer off-the-shelf computers. That would be configured in the BIOS, not in the OS. After a certain amount of idle time, the current state will be saved in memory (like the hibernation feature of the OS), and the networking and attached devices will also be disabled, the hard drive will spin down, and to all appearances the computer will look as though it's been shut down. Since all attached devices are affected, the computer can't be brought out of this state by moving the mouse or typing on the keyboard. Usually it requires pressing the power button. To turn off this feature, you'd need to access the BIOS at boot (usually by hitting F2, I think) and navigate the interface until you get to a power saving menu.

yes agreed, i feel the monitor not waking from suspend / hibernate is most likely an issue related to him not installing recommended drivers or not knowing what hibernate means

Codecaine_21 : there is very little malicious software or viruses written to infect a linux systems. im going to enforce "Ryan Dwyer" and "OpSecShellshock" 's opinions - i am confident that if you private message either of them they will be overly helpful.

please learn to google before posting to a forum, and recognize that people are paid to answer your requests on sites like this.... please try installing the software as intended bofore making your own changes....

---

### Post by cariboo on 2010-09-27
> **mrhhug said:**
> 
please learn to google before posting to a forum, and recognize that people are paid to answer your requests on sites like this.... please try installing the software as intended bofore making your own changes....

I hope that's a misspelling, because there are no paid support people here, we are all volunteers.

---

