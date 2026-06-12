---
title: "Help With an ubuntu server set up"
date: 2009-02-22
forum: Server Platforms
---

### Post by Dowdy90 on 2009-02-22
As my first post on the forum, I would also like to say hello to everyone.

Right, and now down to business. I am pretty new to ubuntu, I have been around it for a while and have started using it myself recently. I got relativity used to it and decided to try to attach a server to my two stand alone computers. This is where I got stuck.

I have looked through many guides, but none helped me. What I am aiming to do is to create a server domain where the workstations attack to (In brief).

i.e. : I want all my programs and files to be stored on the server and I want all my workstations to be able to log in to the accounts on the server from the log in screen.

I have tried using Webmin but that is not what I was aiming for.

Any and all help would be appreciated. Sorry for the newbishnes this may contain.

(Also on the server tower I can either run ubuntu server or i can download the desktop gui for it, helpo in either is greatly appreciated)

Dowdy

---

### Post by E_K on 2009-02-22
hi welcome to the forum

have you read this thread, it should push you in the right direction, and you should see some good terms to slam into google :)

[http://ubuntuforums.org/showthread.php?t=246589](http://ubuntuforums.org/showthread.php?t=246589)

---

### Post by Dowdy90 on 2009-02-22
Thankyou,

and thankyou for the help.

This has helped me with the file sharing =D

Im not there yet but this is definitely good,

thanks a lot

---

### Post by E_K on 2009-02-22
if you get stuck post back, or have some small questions pm me :)

---

### Post by Dowdy90 on 2009-02-22
This is not really what i am after. I am trying to set up the server to host accounts,file and applications. These accounts and files can then be accessed on any other workstation on the network. 

On windows this is done by creating a server domain, and attaching the workstations to the domain so the server can control them. Using an account manager on the server accounts can be created that can be logged on from and workstation.

how do i achieve this in ubuntu server gui (terminal is no other option)

---

### Post by E_K on 2009-02-22
well, there's a very easy way with linux  
 two, actually...
 1: write a client script that calls a script on the server containing 'dpkg -i ' commands at boot
 2: kickstart
 and then finally, the 'cheating' way, which I use
 boot linux over the network, so there is actually only 1 real 'OS install', thus, when you install a package, ALL machines will be affected
 and you manage it at file level live from any other station

---

### Post by Dowdy90 on 2009-02-22
sweet sounds good how do i go about doing number 2 the cheating way

---

### Post by E_K on 2009-02-22
all the work stations need to be able to netboot, check the bios and see if they can boot from lan,

and then the best thing to do is check out google on "how to netboot ubuntu"
and maybe throw in 'deployed software' in the search

happy reading :)

---

### Post by Dowdy90 on 2009-02-22
thx alot pal il let you know if it goes tits up :P thx for the help

---

### Post by E_K on 2009-02-22
you have to try really hard to make it go tits up, it will be ok, there should be lots of VERY good tutorials on the net on how to do this.

Thats why i let you search for it, because it will be more detailed than i can quickly explain.

and it will improve your search skills :D

---

### Post by Dowdy90 on 2009-02-22
i have searched google. all i can find is installation net bootin. if you know of a tutorial on how to set up the server to host a netboot. that would help alot.

also is there no easy way to do it as a domain. standard ubuntu has some domain features in it so it looks possible. 

thx again for any reply

---

### Post by E_K on 2009-02-22
this should be a start

[http://ubuntuforums.org/showthread.php?t=445111](http://ubuntuforums.org/showthread.php?t=445111)

there maybe an easy GUI way to do this, but im dead against GUI's on servers

granted most of the how tos are about netinstall but if you have a read you may understand the concept some more, its not sooo far off netbooting.

sometimes you want to get a job done quickly, and in the long run the fastest way is to take the time to learn about what your doing and how it works before you start.

Or dive i head first screw somestuff up find out how to fix it, until you get there

both work :P though option 2 may leave you balder than the 1st hehe

---

### Post by Dowdy90 on 2009-02-22
haha i agree dude. i have used windows sever alot. and really like the way it is done the account management is really easy to create and configure accounts over worstations. im sure ubuntu has something similar. 

i have been reading up trying to find as much background information as possible 

i will read though these tutorials and have a bash at it. but domaining seems easier as there is no ip configuration or protocols to set up for the server to host these accounts

---

### Post by E_K on 2009-02-22
there shouldnt be that much, just for the server, then for clients you choose lan as primary boot device from the bios, and watch it rock :)

---

### Post by Dowdy90 on 2009-02-22
non of these threads or posts i am looking at actually tell me how to set up the server to host a GUI interface to the other machines

---

### Post by E_K on 2009-02-22
oh yeh forgot about the GUI bit, ill look into it for you

---

### Post by Dowdy90 on 2009-02-22
np dude il keep looking myself

il get back to you if i find anything

thanks agian

---

### Post by E_K on 2009-02-22
in theory all users are just 'local users' in the 'virtual image' that every computer loads,

so when you setup the netboot, just choose whatever distro you want the clients to use as the image being netbooted

---

### Post by Dowdy90 on 2009-02-22
but that still only installing unbuntu on individual mashince creation a new user on the mashince rather than another one on the server

---

### Post by Dowdy90 on 2009-02-22
how do i configure the server to allow the other computers to netboot from it withouth actually installing it on the pc

---

### Post by E_K on 2009-02-22
all you need is to set up dhcp/tftp and create a virtual client

---

### Post by TwiceOver on 2009-02-22
I just wanted to add to how Windows domains allow you to log onto different machines and have all of your files available.  It might help lead to an Ubuntu solution for this.

Machines and user accounts authenticate to the domain controller to check to see if they are a member or authorized user of the domain (domain logon).  I'm not sure how you would create these machine and user accounts on a Linux box, I'm sure something similar is possible.

For your files, often times admins will use "Document Redirection" which basically moves your Desktop/My Documents/Start Menu/Application Settings to network shares (usually a central location like \\server\users\%username%).  This could probably be done by mounting /home to a share on your server.  That way whichever machine you are on will use the files on the mounted partition on your server.

Just a couple ideas for you.

---

### Post by E_K on 2009-02-22
sorry im out :S, im not sure how to pull it off that way, try googling some more if i find something i will let you know

---

### Post by Dowdy90 on 2009-02-22
everything i read about netbooting and setting up the dhcp is just to insall ubuntu onto the hard drive from the internet.

theres nothign about the server hosting anythging the unbuntu gui

---

### Post by E_K on 2009-02-22
it is possible to do without installing anything clientside, but i dont believe the results you will get are exactly what you want...

---

### Post by Dowdy90 on 2009-02-22
does any one know it its possible for samba to host a domain that ubuntu 8.10 (not server) can access and connect to

---

