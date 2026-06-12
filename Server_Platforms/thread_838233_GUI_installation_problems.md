---
title: "GUI installation problems"
date: 2008-06-23
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-06-23
Sorry to ask something really basic but I have had a play with the desktop version of Ubuntu and thought I'd see what the server version was like (with a view to changing the server at home (then work) to Ubuntu)

However as I am a day-one newbie to this I have installed the server version on a test machine at home

I have done: "sudo tasksel install ubuntu-desktop" on the home pc which completed and I ran StartX to get the GUI which worked fine (at home)

This morning at work I have installed ubuntu server on another pc.
The server install went fine.

Then I logged in with the username I created,
typed "sudo tasksel install ubuntu-desktop"
it asked me for the password and it said something about extracting and went to a blue "Package Configuration" screen and says "Installing packages" "Please wait" then just sits there at 0% forever. 
I don't know how to terminate the install either other than doing CAD.

The only difference with the machine at home and work is the system board. The one at work has an inbuilt RAID controller.

btw does it matter whether I have the install CD in when typing the tasksel install command?

btw I have done sudo tasksel and tried to install ubuntu-desktop from there - Same result
tried to install one or two of the other desktop options but it comes back and says Aptitude Failed (100)

Later on....

I have now done the server install on a completely different pc with completely different hardware.
The first time I tried sudo tasksel and tried to initiate the ubuntu-desktop install from there and it just hung there and gave me blank lines if I hit the enter key.
Second time was using the command line "sudo tasksel install ubuntu-desktop" and it just did the same as the previous post: went to a blue "Package Configuration" screen and says "Installing packages" "Please wait" then just sits there at 0% forever.

Can anyone give me some advice please?

Paul

---

### Post by windependence on 2008-06-23
> **G1ZmO65 said:**
> 
Can anyone give me some advice please?

Paul


>format c:\ /s/u

I386>winnt32.exe

:):)

Don't do that (kidding), but why so insistent on loading a GUI on the server. What do you guys do with the machine at work? If it's a file server, you could run it without a GUI and connect to it with all the Windoze machines

-Tim

---

### Post by G1ZmO65 on 2008-06-23
The reason for using a GUI is that I know absolutely nowt about Linux and tbh am lost without one.

The reason for considering Linux is primarily financial as the boss doesnt want to pay for Win2003 server and CALs

Problem is that I, as network admin, need to do some learning and boss wont allocate me time to do it so running a test server with a GUI is quicker than trying to learn Linux from scratch.

---

### Post by windependence on 2008-06-23
Well then you could always install Ubuntu server with Webmin and admin it from a web browser. Webmin is truly an awesone tool if you are using it on your local network. More care is needed if you are allowing access from the outside, but it can be done. It's much lighter than a full GUI and you can wean yourself off of it as you gain experience.

-Tim

---

### Post by weryl on 2008-06-23
> **windependence said:**
> Well then you could always install Ubuntu server with Webmin and admin it from a web browser. Webmin is truly an awesone tool if you are using it on your local network. More care is needed if you are allowing access from the outside, but it can be done. It's much lighter than a full GUI and you can wean yourself off of it as you gain experience.

-Tim

What do you mean about the extra care for access from the outside? Say I want to run a sftp server, cant i set it up from webmin?

---

### Post by garethsimpsonuk on 2008-06-23
What Windependence said is very true about the GUI. I remember not so long ago these guys were advising me to not install a GUI but I thought it would help.. it doesn't. There are very little tools in the GUI for server admin. 
You will find you end up using the cmd line anyway as it's faster and you know exactly what you're doing.. well sometimes lol ( + when you get intsructions from how to's and here, they will be in cdm format anyway. Webmin is great, [this]("http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html") is the best guide I've found. Just change the version number for the latest one ( 1.420 ).
What Windependence is saying is Webmin has a webbased gui, you're usually using it on your LAN but you can open the webmin port ( 10000 as default but change it )and acess webmin from outside your LAN. 
As I'm sure you're aware the more ports open the more potential exploits so look into securing it if you need it open. If you're outside your LAN openssh and putty is a better option. 
I haven't sorted sftp on mine yet, I think there is a module in webmin for it. There is a hell of a lot you can do with webmin, combined with putty and midnight commander you wont need a GUI, and you can save all those extra resources.

Hope this helps,

---

### Post by G1ZmO65 on 2008-06-23
Think I'm just having a bad night lol

Tried in vain to install webmin on my XP machine to admin my home ubuntu server but the installer keeps bombing out firstly saying that it couldnt find an etc dir then the perl module which is called at the end of the install keeps crashing.

Taken it all off and starting again grrr

btw I'm using the WebminInstall.exe and have installed the latest ActivePerl

Back in a bit with more.....

Nah still wont install. Will try at work tomorrow and/or mail the writer of the installer.

Rapidly losing interest in this stuff!

---

### Post by garethsimpsonuk on 2008-06-23
you dont install webminon windows! follow the guide I linked to. You install it on the server then type [https://lan.ip.of.server/10000](https://lan.ip.of.server/10000) in a browser on your windows box. I don't know where you've got webmin .exe from but it's not webmin. google webmin mate and do a bit of research. it's not that hard to install at all, just follow that guide. id be careful of that .exe aswell

---

### Post by G1ZmO65 on 2008-06-24
I got the WebminInstall.exe here [http://www.webmin.com/windows.html](http://www.webmin.com/windows.html)

Sorry, I obviously misunderstood webmin :p

Will follow your link instructions :)

---

### Post by windependence on 2008-06-24
Gareth is correct, you install Webmin on the server and access it from another machine or from the local machine using [https://localhost:10000](https://localhost:10000)

-Tim

---

### Post by G1ZmO65 on 2008-06-24
Thanks

Followed the instructions but it wouldnt connect so I've done a full clean reinstall again and am following the instructions to the letter.....

Yay! :)

Got logged in with Webmin

Wonderful thanks folks (though I suspect this is not the end of my questions lol)

Cheers
Paul

---

### Post by windependence on 2008-06-24
This may have been just a small error. You need to get yourslef out of that Windoze "reinstall everything" mentality. :)

After you get the install done, if it does not work please post the error here so we can help you.

-Tim

---

### Post by chuck jessup on 2008-06-24
I do believe that you have to install it on the box you wish to admin... i have yet to do that for my server box, i need to... but i have a broken install that needs to be fixed first... if time will allow it...

---

