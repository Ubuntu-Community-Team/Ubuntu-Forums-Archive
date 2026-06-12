---
title: "Lock down a laptop"
date: 2008-07-29
forum: Security
---

### Post by rustybutt on 2008-07-29
I need to get a laptop for my kid to use at school this year.  
He has a gaming addiction, so I'm planning to get him one of those new Dell Ubuntu laptops and lock it down so that he only gets those applications I allow him to have.  He should be able to use a web browser, e-mail client, Open Office, gimp, and so on. 

First I'm going to remove the typically installed games.  Then I'll disable sudo access for his account, so that eliminates him using apt-get or synaptic.

I'll probably set administrative password on the system BIOS, and then setting system boot order so that it only can boot off the system drive, and not any other media.

How can I set up single user mode so that it demands root password before giving a prompt?  That's the default mode in Solaris and would be useful to me here.

Thanks!

rustybutt

---

### Post by Titan8990 on 2008-07-29
I believe unlocking the root account is enough for it to prompt a password in recovery mode. Also, you should know as soon as I read this I thought of a way around what you are doing. If someone has access to the local machine and enough will they can essentially do anything they want.

---

### Post by eldragon on 2008-07-29
im not trying to get inbetween your parenting practice. but is it such a good idea to have a kid so locked he will do anything to try and get rid of the lock? i know that wouldnt have stopped me back in my teen days..


he could technically remove the HDD plug it into a friends computer and have the root password changed.
even setting up wireless requires a root password.

instead, why not buy a full desktop leave it in a place of the house with enough family movement he gets checked from time to time?

---

### Post by Titan8990 on 2008-07-29
Personally, I would reset the CMOS, put my own password on it and then boot to my USB. You get the idea, these restrictions can only be somewhat effective.

---

### Post by rustybutt on 2008-07-29
My kid is capable to use a Linux laptop, but he's not competent to do any serious hacking.  He hardly knows the cp command and doesn't know vi, let alone anything about administering an 'IX machine under the hood.  

I don't need to secure it against a Black Hat.  Just against my kid who only thinks about video games.  I'm just trying to close the obvious doors, like single user mode, booting off of CD, sudo, etc.

---

### Post by rustybutt on 2008-07-29
All of you are correct about the machine being crackable, and that if he were determined, he could crack it.  But he's not into Linux technology. He's just into gaming.

My son is mildly autistic and is currently obsessed with video gaming.  He is at the point where this past school year, he did ***_*NO*_*** school work.  It wasn't that he didn't do well in school.  He did absolutely nothing.

This coming year he's going to a school here in the area which specializes in children like him, and I think he'll pull it together.  But he needs to have a laptop as an educational tool, not as yet another gaming distraction.  He understands this, and the school is structured in such a way that he'll be able to get all of his work done during the day while he's there and in their after school work program.  That way, when he comes home, he'll have his evenings and weekends free to enjoy his gaming.

I'm all for him being happy and enjoying himself.  I just want to give him an Ubuntu laptop as a tool for working in school.  

Our home environment is a mix of Windows and Ubuntu.  My son has a Windows desktop because it's primarily a gaming platform for him.  My desktop is an AMD quad core/8 GB RAM Ubuntu Hardy machine.  I've installed LTSP on it so that my wife runs an X-term for her desktop and my kid runs an X-term VM on his windows machine when he wants an Ubuntu environment to work from (which is rare).  And with this desktop, I can run all the VMs I want for this and that as well.

So right now I just want to lock the kid out of getting single user mode on his laptop.

rustybutt

---

### Post by tamoneya on 2008-07-29
just disable single user mode.  Remove it from grub and then lock the boot options in grub with a password.  That will make it so that you can select the boot options that are currently there but cant change them.  

However I would worry about other things before I started worrying about single user mode and CMOS batteries.  What about online flash games.  And then if you block those he can always use one of a million proxies.  Honestly I really like the idea of the desktop in a place in the house where he cant play games without getting noticed.

---

### Post by rustybutt on 2008-07-29
The reason he's getting a laptop is for him to take to school and carry from class to class.  I realize that there are java and flash based game sites and that there's not a lot I can do about those, but it does put a limit on stuff and hopefully the staff there can keep him focused on his school tasks.  Again, the point is primarily to remove temptation from him for the limited time he is to use it in school.

He already has a Windows desktop at home, in his room, that he can game on.  He also has Ubuntu access through an X-term VM I set-up on his Windows desktop.  At home, he has everything he could want.

Thanks for the suggestions about grub!

---

### Post by Biochem on 2008-07-29
Is it the school whose asking for the laptop? if the answer is yes than they might want to use special software that are windows only. They might work in wine, but they might not.

---

### Post by Dr Small on 2008-07-29
If you don't mind me asking, how old is this child that is obsessed with video games?

---

### Post by rustybutt on 2008-07-30
The school did ask for us to provide him with a laptop, but they have not said they want him to use any specific software.  It's to be used for researching questions on the web, word processing, and possibly for making presentations.  Not much else.

There's not a desk job anywhere anymore that doesn't have a computer to use for the basics.  And that's how schools are going to be using computers in the future.  I sure as **** wish I had a word processor when I was in school.  Back then it was paper and pencil.  I still have my slide rule and am not afraid to use it!

My son is 16 years old and will be entering his junior year in high school.  A nice kid but still pretty childish with regards to the things he has to do.

rustybutt

---

### Post by PmDematagoda on 2008-07-30
Well, I don't want to burst your bubble, but getting rid of sudo access may not be enough to ensure that any games can't be installed. For example, in Enemy Territory, I can install the game in my home directory and not touch a place owned by root at all and still be able to run the game properly.

How about disabling 3D acceleration? That might help, although it does have the side effect of removing Compiz in the process.

The case is, there is no way you can completely lock down a child since he/she will always try and find a way to get over it, you can always try, but there is no guarantee:).

---

### Post by Dr Small on 2008-07-30
Wow. 16 years old. I myself am 17, currently. Back when I was 13-14 and on Windows, I remember installing keyloggers and hacking the school software so I could get Admin access (I'm homeschooled :D).

Even me at 16, locking down a computer that tight would not have stopped me. Gosh, I was writing an article on my blog of locking down my own computer and finding physical ways around it.

Having an addiction for computer games is really not something you want to feed. Trust me. I have seen what it does to my friend and my own cousin (who is addicted to nothing but Runescape, and the first week he was off school, did nothing but sit in front of his computer all day long, playing runescape). I myself, back when I was 12 and 13, was addicted to Close Combat: First to Fight, and loved the online gaming. When we changed ISPs, all that came to a halt because of bandwidth restrictions.

Anyhow, back to the matter at hand. As long as their is physical access, there is no security, unless the disks are encrypted. I can begin to think of numerous ways I would bypass your locks, if they would be imposed on me. But for a person who has no intrest in the under-workings of a computer / linux, the locks will hold them in.

Dr Small

---

### Post by rustybutt on 2008-07-30
I know that given physical access to a machine, someone competent can crack it, but my kid isn't that kind of user.  He loves to play games, but that's about it.  He does very little at a command line and asks for help in installing Windows.  He reads a lot of stuff on the web and will tell you all day long about what language is good for what, but couldn't write a "for loop" to save his soul.  This is NOT a kid who's going to crack a moderately locked down Ubuntu laptop while at school.

There will be other web based games and means of wasting his time that he'll pursue, but I figure that his teachers will have to help him manage his time while he's at school.

Besides, he'll have a high "Cool Factor" having the only Linux Laptop in a school riddled with Windows and the occasional Mac.

---

### Post by Thorzilla on 2008-08-04
Well I'm no expert, but you might try this:
[http://www.linux.com/feature/62060](http://www.linux.com/feature/62060)

Physical access points will be hard to block, but if he isn't into hacking, then he probably wouldn't explore those possibilities.

---

### Post by /////// on 2008-08-05
Well you could always re-partition the hdd so that the only space left in it is only just enough for the OS. Then prevent him from uninstalling anything and he won't have enough space to install any games.

---

