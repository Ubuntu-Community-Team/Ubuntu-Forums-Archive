---
title: "Computrace® LoJack® for Laptops"
date: 2008-02-15
forum: Security Discussions
---

### Post by Madmoose on 2008-02-15
Hello everyone, 

It's been a long time since I've been on the forums, and heres why. 

About a year ago I returned to school, and when I first started I had a duel boot of XP and Ubuntu. I love Ubuntu, but on my third day of school a classmate had his computer stolen! This got me thinking about this, and I purchased Computrace® LoJack® for Laptops. Little did I know that the software would prevent me from having my Ubuntu partition installed, and so in the interest of security I was forced to stop using linux. 

Oh how I miss Ubuntu, but I'm unwilling to go without LoJack installed. Yesterday in my welding class another student had his wallet, iPod, and laptop stolen while we where in lab.

Now, to my point. I would love to go back to Ubuntu, but at this time Computrace doesn't support Linux. A few months ago by popular demand they started to support Apple PC's. Maybe, just maybe. If all of you could help me out we can raise one voice, and let them know that we would like to have our laptops protected. Even if you're not too keen on the whole 'checking in every time you get online" just an email would help!

Here is what I would like you to do:

Write an email to this address [EMAIL="support@lojackforlaptops.com"][COLOR="DarkOrange"]support@lojackforlaptops.com[/COLOR][/EMAIL]

Tell them that you would like them to support Ubuntu and other Linux kernels.

 (If someone is a good writer, and could make a generic email for people to copy & paste that would be helpful) 

I would REALLY like to get away from windows again, but I can afford to have my computer stolen without the chance of getting it back. So, I ask again. Please take some time, and write that email. [http://ubuntuforums.org/](http://ubuntuforums.org/) has 10,667 currently active users, and if only half of those users wrote that email;  the voice would be to loud to ignore! 

Thank you for your time, 

Moose :KS

---

### Post by honeydew on 2008-02-15
so what does lowjack for laptops do exactly? does it rely on networking? or do you have some type of GPS transmitter in your laptop?  I have seen scripts where people have done this for free.. mind you, you would have to have a server at home or a server somewhere to send files to.. but you could have a script that sftps/http/ftp/etc a file recording the location(IP) of your laptop everytime it is hooked online.  However this may not work if the assailant is trying to connect to a wireless network.  So you may want to create a guest account that is easily accessable.. which allows a user to log in and use the system normally(locked down).  This could allow users to connect to a wireless access point and send your location information down the pipe.  At this point you could contact the ISP and the authorities etc etc with the IP of your missing laptop.  Is this what your talking about?  *thinks about writing a script for his laptop*

---

### Post by TinkerJ on 2008-02-18
I have a Dell D830 which has Computrace software in the BIOS. On their website they tout it as being persistent, even when the OS is reinstalled. What?? I think that this sounds too simple; they must assume that everyone's using Windows.

Now, you can also set a password on SATA drives that makes them impossible to access without it, even if they put it into another machine. Does this help you recover a laptop? Not unless they just get fed up and turn it in to the nearest police station.

There is also another BIOS password that makes it so that you can only boot from certain devices (for example, exclude the CD drive so that the thief can't reinstall an OS). Again, will they really just get too fed up and turn it in?

So I guess that the trick IS to make a separate OS partition or user account that is easily accessible so as to get them to go on the internet.

---

### Post by Madmoose on 2008-02-27
Hello, 

I hope you don't mind me copy and pasting text right from their site, but I don't feel like re writing what is already said. 

What is it:
> Computrace® LoJack® for Laptops is a theft protection service that tracks, locates and recovers stolen laptop and desktop computers.

Software installed on your computer works behind the scenes to silently and securely contact our Monitoring Center, and if stolen, reports its location using any Internet connection.

Our Recovery Team then tracks your computer’s location and partners with local law enforcement to get your computer back. If your stolen computer is not recovered in 30 days, you’ll receive a full refund for the purchase price of the software.

How does it work?
> 
If your computer is ever stolen…

    * You file a police report and notify our Recovery Team.
    * When your stolen computer contacts our Monitoring Center, it is placed on high-alert and starts calling us every 15 minutes, allowing our Recovery Team to closely track your computer’s location.
    * Our Recovery Team provides law enforcement with tracking information and documentation essential for procuring search warrants and leading them to the location of your computer.
    * The police recover your computer and return it to you!

Recovery Team 

> Rest Assured with our Recovery Team

Staffed by former police officers and seasoned security professionals, our Recovery Team works directly with your local law enforcement and Internet Service Providers to obtain subpoenas and warrants. With over 200 years of combined law enforcement experience, our Recovery Team achieves the highest success rates in the industry - simply because they know how law enforcement works.
Let us do the Dirty Work

When a computer is stolen, it just takes one phone call to get the Recovery Team working for you. Our Recovery Team can find your stolen computer because they have close partnerships with over a thousand police departments across North America.

We’ll put your computer on high-alert status and pinpoint its location when it connects to the Internet. Now you can sit back and relax, and we’ll call you when we’ve found your computer.

If your computer is not recovered within 30 days, you’ll receive a full refund for the price of the software.

I hope that answered some of your questions. In a nutshell every time you connect to the internet is sends in a call to their call center. It ignores you until a theft has been reported, and then they work with police to get it back. 

As for this: 
> So I guess that the trick IS to make a separate OS partition or user account that is easily accessible so as to get them to go on the internet.

Yes, you're right about it still being there when the OS is reinstalled. So, if they did steal your computer, and reformat it it will still make those calls. 

As for the separate OS partition. That's part of the problem I'm having. It will not let you have more then one partition. :(

Anyway,

I got a reply from them the other day, and it said : > We have recently become  well aware that there is a large community of Ubuntu users out there.

They must be getting your emails! Thanks to everyone who has sent an email, and please if you have not sent one (even if you don't plan on using it) do so!! The more people ask for it they better the chance of I'll become free from the shekels of vista!

"Viva la Resistance!"
Thanks again, 

Moose

---

### Post by DFLiddle on 2008-04-17
I'd be happy to write a request that Computrace support Ubuntu.

Our organization has a contract with them for the Data Deletion service on some of our more well-traveled laptops. Recovery is only supported in a few countries (e.g. U.S., U.K., and Canada), but Data Deletion extends worldwide.

If the computer is compromised, an authorized Data Deletion administrator in our organization logs in to the Computrace website, and with the additional authentication of an RSA token, initiates a Data Delete request. The next time the computer connects to the Internet and "calls home", it receives the command to begin deleting files to the extent requested -- up to killing the whole operating system. Nice.

We tested this procedure on a Dell Latitude D620 connected to a projector, and watched with delight as files began disappearing from the Windows Desktop. At the end, the next action we tried to take on the machine caused Windows to crash. Pure beauty.

---

### Post by nicedude on 2008-04-19
While the idea of recovering your computer is awesome, I thought I might point out that while a thief might first look for private data on your laptop they steal (which could be protected with encryption) the second step is usually to delete your HDD with a utility like Dban boot-n-nuke which would thwart the Computrace Lojack by deleting it along with everything else. They can then install any OS they wish. The only solutions I am aware of that are foolproof are hardware based which come with a few high end laptops. So even with this protection if the thief is semi-intelligent any software based solution will prove ineffective at recovering the PC. But if it did work it would be almost worth getting it stolen to see the look on their face as the cops knock on the door with a search warrant :-)

---

### Post by DFLiddle on 2008-04-19
If a computer is equipped with a Trusted Platform Module (TPM) on the system board, the Computrace agent will persist through certain levels of formatting and erasure, though I don't know how much it can withstand. It definitely survives a basic reformatting. The TPM is also capable of hardware-level encryption.

I wonder what would happen if I installed it on my D610 with Wine?

---

### Post by Madmoose on 2008-05-11
I have some good news!

My uncle found out a way to get Ubuntu to install even if you have the  LoJack® for Laptops installed.

The key is wubi: [http://wubi-installer.org/]("http://wubi-installer.org/")

I have 8.04 and Vista installed on my HP Pavilion dv2000, and it seems to be working 100%! It even looks like the Computrace software still contacts the call center even under the Ubuntu OS.

On a side note: Thanks for 8.04! I've been out a while because issue, but this is the FIRST distribution that just worked on my laptop 100% out of the box. :) Good job to everyone who has made this the best OS I've seen!

I hope that helps some of you!

Moose:-\"

---

### Post by artard on 2008-06-17
I don't think a Wubi install is a real solution for this as we can't use Ubuntu standalone.

So has anyone tried using a utility to completely reformat the HDD, and then install Ubuntu from there?  Arg!  I _just_ ordered a new Dell XPS laptop and got the lojack option (it was bundled with the a package that was cheaper than customizing the laptop).  I hope they don't pre-install that software for me but if so... I will attempt some sort of low-level format and post my results here.

---

### Post by artard on 2008-06-19
Just got my Dell XPS M1330 with Vista and the lojack software pre-installed.  I popped in the 8.04 CD, manual partition, deleted all partition and installed Hardy from there.

No problems whatsoever... so I'm not sure what the problem could be for other users here.  I did notice in my BIOS security there is a Computrace settings area but it is disabled there.

---

### Post by auburn on 2008-07-20
"If the hard drive is reformatted or replaced, the Computrace Agent support in the BIOS rebuilds the necessary application files on the hard drive as required by the customer."
[http://www.absolute.com/products-core-technology.asp](http://www.absolute.com/products-core-technology.asp)

The way I interpret this is: if you low-level format, or even completely replace the hdd, the bios will initiate a re-install of the computrace agent into your OS AFTER you install one of the supported OSs. The Agent will then contact absolute.com whenever the user starts that OS.

Since I install ubuntu in all kinds of computrace-supported dells, I think it's possible it wasn't computrace that kept madmoose from installing. But maybe old versions of computrace had bugs that it doesn't have now.


**
"Computrace is supported on 32-bit versions of Windows 2000, XP, Windows Server 2003 and all 32 and 64 bit editions of Windows Vista. Computrace is also supported on the following Apple platforms; Mac OSX 10.3, 10.4 and 10.5"
check the above link for updates

---

