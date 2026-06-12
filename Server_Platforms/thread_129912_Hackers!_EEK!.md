---
title: "Hackers! EEK!"
date: 2006-02-14
forum: Server Platforms
---

### Post by Connollyir on 2006-02-14
I just spent the better part of an hour trying to figure out why Konqueror was randomly launching and dirrecting me to a warez site. I am relatively new to Linux, but it was my understanding that spyware and viruses are infrequent at best - which meant this was a directed and personal attack on my machine. I checked out my logs and couldn't find any sketchy footprints, although I did find multiple entries from two users, one from Amsterdam and one from Taipai, who tried unsuccessfully to log into my computer via SSH. 

From what I can tell, this mystery user brute forced his way into my system under my password (which could have been more secure) and sudoed his way around till he got what he wanted, took out the pertinent log files and left.

Eventually a friend and I found the cron job that was responsible for the poppups and got rid of them. 

Password has since been changed and now I am much more motivated to put together the firewall box I've been putting off for some time.

Pretty shady stuff eh?

-Ian

---

### Post by Iandefor on 2006-02-14
Freaky.

---

### Post by mstlyevil on 2006-02-14
[QUOTE=Connollyir]I just spent the better part of an hour trying to figure out why Konqueror was randomly launching and dirrecting me to a warez site. I am relatively new to Linux, but it was my understanding that spyware and viruses are infrequent at best - which meant this was a directed and personal attack on my machine. I checked out my logs and couldn't find any sketchy footprints, although I did find multiple entries from two users, one from Amsterdam and one from Taipai, who tried unsuccessfully to log into my computer via SSH. 

From what I can tell, this mystery user brute forced his way into my system under my password (which could have been more secure) and sudoed his way around till he got what he wanted, took out the pertinent log files and left.

Eventually a friend and I found the cron job that was responsible for the poppups and got rid of them. 

Password has since been changed and now I am much more motivated to put together the firewall box I've been putting off for some time.

Pretty shady stuff eh?

-Ian[/QUOTE]

Proof that Linux is not immune to cyberattacks if you do not practice a good security policy. I would suggest you install and run Firestarter until you can get your hardware firewall up and running. Also if you have root enabled, it might be time to disable it.

---

### Post by towsonu2003 on 2006-02-14
if someone got root in your machine, no one knows what else they installed... I would reinstall the operating system. Also, a moderator should move this to security section. 

I would also find how they got in before reinstalling to prevent it in the future. someone may be able to help with finding that in the security forum.

---

### Post by Connollyir on 2006-02-15
The kid down the hall seemed to be confident they used SSH to enter my box, and he knows far more about Unix/Linux systems than I do. I didn't really mean to start this as a security thread, just sort of an announcement/warning to others to be more careful than I was.

I was just looking at firestarter. I started tinkering with privoxy and the tor proxy servers a while back to give myself some anonymity in the net but I just didn't have time to set it up. I think I am going to run Iptables since there are many configuration utilities written for it, one of which - kmyfirewall - is for kdm which is what i run so that should work nicely. 

But I never had the root account enabled. I think he forced his way into my account and sudoed his way around which would make an argument for the root account not against it, right?

-Ian

---

### Post by mstlyevil on 2006-02-15
[QUOTE=Connollyir]The kid down the hall seemed to be confident they used SSH to enter my box, and he knows far more about Unix/Linux systems than I do. I didn't really mean to start this as a security thread, just sort of an announcement/warning to others to be more careful than I was.

I was just looking at firestarter. I started tinkering with privoxy and the tor proxy servers a while back to give myself some anonymity in the net but I just didn't have time to set it up. I think I am going to run Iptables since there are many configuration utilities written for it, one of which - kmyfirewall - is for kdm which is what i run so that should work nicely. 

But I never had the root account enabled. I think he forced his way into my account and sudoed his way around which would make an argument for the root account not against it, right?

-Ian[/QUOTE]

I think it would make a better argument for using a more secure password. One trick I found is to take a phrase or a line to a poem or a song then use the first letter of each word while alternating between capital and lower case letters. Then you inject a few numbers into the mix. This is how I do it any way and it has not failed me yet.

---

### Post by matthew on 2006-02-15
[quote=Connollyir]which would make an argument for the root account not against it, right?[/quote]Actually it is a great argument for making really strong passwords that can't be discovered using a brute force/dictionary type attack.

[http://en.wikipedia.org/wiki/Password_policy](http://en.wikipedia.org/wiki/Password_policy)

---

### Post by Virogenesis on 2006-02-15
Don't install a SSH server if do not know what you're doing its silly and ubuntu doesn't get shipped with ssh.
If you do decide to use ssh use something like port knocking to stealth the port.

O yeah what you had wasn't a hacker its a cracker.
Hackers often get annoyed when you mix the two up. 

Basicaly what you need is a good password and sense like windows. 
ubuntu comes shipped with services disabled for a reason unless you know about good security don't run any.

check for rootkits or other user accounts.

Ps: go visit the dude and introduce him to Mr. Bat 
Hes a charming fellow really

---

### Post by Bandit on 2006-02-15
Disable SSH, then run a hardware firewall.
Then block off all open ports that you dont need.
I got my network system locked down tighter then most bank networks.
But nothing is ever 100% safe.

---

### Post by TechSonic on 2006-02-15
I use a password that uses this format.  84LKDIuu84gfufYWEnv8723UM20EWBAbal5eal  but not exactly in that order but Thats how long I use.  Or until the password box says I can't put anymore in.  Then I print the password and stick it to the bottom of my keyboard.


I've never had my security broken, not ever.

---

### Post by codejunkie on 2006-02-15
i don't know how true it is but i've heard that it's safer to use password phrases for example "The Cow Jumped Over The Moon!" instead of random letters an numbers.

---

### Post by Bandit on 2006-02-15
I dont think it would be. Of course the more characters the better.
Most password tools use most possible dictionary words to start with like (god, password, newuser,etc..) then it starts at the first word in the dictionary then goes through them all. Then those words with numbers, then numbers, then combinations of words. Depending on your inet connection it can takes days to crack as password. 
Thanks to cookies, most users dont know what cookies they let enabled. Cookies are great for reporting keystrokes back to another computer. You can get passwords. Its simple as looking over the log and seeing "www.mynewbank.comuserbob81mypasswordsucks"  hint.. hint... Then there goes your cash.
This is why firewalls are a must with todays computers. Win, Mac, *nix.. Doesnt matter...
No PC is safe unless its power is unplugged and locked in a vault!!

Cheers,
Bandit

---

### Post by Klaidas on 2006-02-15
[QUOTE=TechSonic]  Then I print the password and stick it to the bottom of my keyboard.
I've never had my security broken, not ever.[/QUOTE]

What if someone looks under your keyboard? :)

---

### Post by Arktis on 2006-02-15
If someone has physical access to your computer, you're screwed anyways.

Especially with ubuntu... all anyone has to do to compromise an ubuntu machine when they have physical access is simply reboot the machine into recovery mode.  Presto.

---

### Post by kaamos on 2006-02-15
[QUOTE=Arktis]If someone has physical access to your computer, you're screwed anyways.

Especially with ubuntu... all anyone has to do to compromise an ubuntu machine when they have physical access is simply reboot the machine into recovery mode.  Presto.[/QUOTE]

Which is why bios (by default set to boot only from hd) and grub passwords are a good idea with a laptop. Makes the job even a bit more difficult..

---

### Post by GeneralZod on 2006-02-15
I always use public key authentication for SSH, but I see no one here has suggested it.  Is it a bad move?

---

### Post by xequence on 2006-02-15
> Also, a moderator should move this to security section.

We HAVE a security section? o_O

> I've never had my security broken, not ever.

And it probably takes you a minute to type!

---

### Post by chimera on 2006-02-15
-Use firestarter
-Disable root if you enabled it
-Change your password to something like ´ß¤&#273;>~&#711;^

worked for me :mrgreen:

---

### Post by ssam on 2006-02-15
dont install ssh if you dont need it.

if you do need it set it up with keys, or restrict where log ins can come from.

set it to only let you log in as your non admin user. that would limit what a remote user could do. if you need to log in and run a few admin tasks then you a  only allow those apps in the sudoers file (make sure you dont allow something that can get a shell.)

if you are using the same password for log on as you use for a website or email, then it may have been packet sniffed. most POP, FTP and SMTP send passwords as plain text.

---

### Post by snowjunkie on 2006-02-15
[QUOTE=TechSonic]I use a password that uses this format.  84LKDIuu84gfufYWEnv8723UM20EWBAbal5eal  but not exactly in that order but Thats how long I use.  Or until the password box says I can't put anymore in.  Then I print the password and stick it to the bottom of my keyboard.


I've never had my security broken, not ever.[/QUOTE]

Are you serious?  How long does it take you to log in?  2.5 hours?

---

### Post by Derek Djons on 2006-02-15
[QUOTE=TechSonic]I use a password that uses this format.  84LKDIuu84gfufYWEnv8723UM20EWBAbal5eal  but not exactly in that order but Thats how long I use.  Or until the password box says I can't put anymore in.  Then I print the password and stick it to the bottom of my keyboard.


I've never had my security broken, not ever.[/QUOTE]

I know I don't have the time to manage my passwords all the time like that. But there are enough other possibilities.

Especially if somebody isn't using the internet the whole day the best protection is to just enable / disable your ethernet card. The connection will be online within seconds and you won't have to be inputting passwords the 'hardcore' way.

---

### Post by Iandefor on 2006-02-15
For a really good password, I play around with numerology to take someone's name and turn it into a string of numbers. After that, I do a few manipulations to make it a little easier to remember.

Even just a string of 6 numbers has around 6 ^ 9, or 10,077,696, possible configurations. So, once a hacker had gone to the trouble of deducing you had a six-character password that was composed of entirely numbers, he would then have the task of checking over 10 million individual configurations. An even more secure setup would be to use a string of 9 numbers, giving the hacker 9 ^ 9 (387,420,489) configurations to check.

---

### Post by mstlyevil on 2006-02-15
[QUOTE=Arktis]If someone has physical access to your computer, you're screwed anyways.

Especially with ubuntu... all anyone has to do to compromise an ubuntu machine when they have physical access is simply reboot the machine into recovery mode.  Presto.[/QUOTE]

In the unofficial users guide for Breezy, they have a whole section on how to prevent this. I disabled the recovery mode in the grub boot up options and just use the GDM screen if I need to run recovery. Also I set a password on my bios and have the computer boot from the hard drive first. The last thing I do is use a random letter password with alternating letters and numbers mixing caps and lowercae letters. I would not say it would be impossible for my system to be cracked but it would take much longer than any cracker would probally spend on it.

---

### Post by MJN on 2006-02-15
[quote=Iandefor]Even just a string of 6 numbers has around 6 ^ 9, or 10,077,696, possible configurations. So, once a hacker had gone to the trouble of deducing you had a six-character password that was composed of entirely numbers, he would then have the task of checking over 10 million individual configurations. An even more secure setup would be to use a string of 9 numbers, giving the hacker 9 ^ 9 (387,420,489) configurations to check.[/quote]
 
:???: 
 
Interesting maths there! A string of 6 numbers, assuming you're using 0-9, has 10^6 permutations i.e. 1,000,000. Likewise, a 9-digit one would have 10^9 i.e. 1,000,000,000.
 
Mathew ;)

---

### Post by Connollyir on 2006-02-15
I had SSH enabled because I built a headless computer using this one and SSH was how I did it....... I just never disabled it aterward. Is it really that much of a security liability to run it? I occasionally use it to controll this computer (at university) from my laptop at home so I would like to hang onto it if I can.

Also are you guys pushing firestarter over iptables? A few of you mentioned firestarter, no one mentioned iptables, and I wondered if firestarter was better? 

Thanks for the advice.

-Ian

---

### Post by towsonu2003 on 2006-02-15
[QUOTE=Connollyir]
Also are you guys pushing firestarter over iptables? A few of you mentioned firestarter, no one mentioned iptables, and I wondered if firestarter was better? 
[/QUOTE]
firestarter is basically just a GUI frontend to iptables configuration.

---

### Post by az on 2006-02-15
[QUOTE=Connollyir]I checked out my logs and couldn't find any sketchy footprints, although I did find multiple entries from two users, one from Amsterdam and one from Taipai, who tried unsuccessfully to log into my computer via SSH. 

From what I can tell, this mystery user brute forced his way into my system under my password (which could have been more secure) and sudoed his way around till he got what he wanted, took out the pertinent log files and left.
[/QUOTE]

I dunno.  A lot of shady sites throw in a complimentary portscan when you visit their site.  If you have sshd running, you will get a number of attempts to log in over the next minute.  This is a very common occurrance.
 
Unless you configure a rule that prevents any ssh traffic in except from your one remote site, a firewall with a few ports open will not help you.

[QUOTE=Connollyir]
Eventually a friend and I found the cron job that was responsible for the poppups and got rid of them. 

Password has since been changed and now I am much more motivated to put together the firewall box I've been putting off for some time.

Pretty shady stuff eh?

-Ian[/QUOTE]
Not a lot of dammage, I think.  A pretty weak attack.  It sounds more to me like a practical joke, really.  Surely if someone could access your box like that, they would take advantage of the fact that they are undetected and just sit there and spy on you.  Are you sure your friend is not pulling your leg?  Ubuntu does not even run sshd unless you install it.

...Just a thought.

But I agree that ssh is not something you should install on your box.  Nice juicy passwords are good, too, as has been stated.  A properly configured firewall could help, but most people would just install one and open up ports to everybody...

..Oh yeah, your box has been compromised.  Reformat it now and start from scratch.

---

### Post by Connollyir on 2006-02-15
[QUOTE=azz]I dunno.  A lot of shady sites throw in a complimentary portscan when you visit their site.  If you have sshd running, you will get a number of attempts to log in over the next minute.  This is a very common occurrance.
 
Unless you configure a rule that prevents any ssh traffic in except from your one remote site, a firewall with a few ports open will not help you.


Not a lot of dammage, I think.  A pretty weak attack.  It sounds more to me like a practical joke, really.  Surely if someone could access your box like that, they would take advantage of the fact that they are undetected and just sit there and spy on you.  Are you sure your friend is not pulling your leg?  Ubuntu does not even run sshd unless you install it.

...Just a thought.

But I agree that ssh is not something you should install on your box.  Nice juicy passwords are good, too, as has been stated.  A properly configured firewall could help, but most people would just install one and open up ports to everybody...

..Oh yeah, your box has been compromised.  Reformat it now and start from scratch.[/QUOTE]

What should I use instead of ssh to control my local media bin? I have a separate box linked to my main computer via crossover, a second nic, and ftp, I perform administrative tasks on that box via ssh because it is a headless unit.... and its going to stay that way. What can I replace ssh with for that function? 

-Ian

---

### Post by az on 2006-02-15
[QUOTE=Connollyir]What should I use instead of ssh to control my local media bin? I have a separate box linked to my main computer via crossover, a second nic, and ftp, I perform administrative tasks on that box via ssh because it is a headless unit.... and its going to stay that way. What can I replace ssh with for that function? 

-Ian[/QUOTE]
Why is that box on the net?  And there is nothing better than ssh for secure access.   It's just that it is a way for others to log into your box.  Most people do not need to run ssh, that's all.  

You can use a firewall block any connections from an ip other than the one you use to access it.  You are running ftp, too?

---

### Post by Connollyir on 2006-02-15
[QUOTE=azz]Why is that box on the net?  And there is nothing better than ssh for secure access.   It's just that it is a way for others to log into your box.  Most people do not need to run ssh, that's all.  

You can use a firewall block any connections from an ip other than the one you use to access it.  You are running ftp, too?[/QUOTE]

Cool. But its not on the net...... its connected nic to nic with a crossover cable...... I have two nics on my main machine and I use one to access the media box with a seperate one for network access. Generally speaking I only have that box on when I am backing up my multimedia........ like right now. The rest of the time its a nice paperweight. 

So in summation, I only have ssh and ftp running on the media box, not on my regular computer (I had ssh on my main box to admin over the media bin but I took it off yesterday). I use a graphical ftp client (gftp) to access the upload files when necissary, then I shut the box down.

Perhaps I can configure my new setup after I reinstall everything so that the I load the ssh module at the command line manually instead of having it load with the other modules on startup?

Oh and do you know if Mozilla Firefox uses encryption when it sends stored passwords to web sites? Or is it just plain text?

-Ian

---

### Post by AgenT on 2006-02-15
Just make ssh more secure. You are giving access to everyone on the entire internet to just log in when you do not need to do this. You describe needing to access your other computers on your network. Then just prevent anyone outside of that network from being able to use ssh.

Also, if someone got in and your password is pretty strong then it may have been sniffed somehow. Did you log in from any public place (keylogger)? Maybe you are using a wireless network that is not encrypted that anyone can sniff. Or you leaked your password out some other way. Notice that ftp is clear text! Anyone can read it with a simple sniff.

Also, if you really want strong passwords, or at least pretty strong passwords, use a password generator. There are a few in the repositories.

---

### Post by spartas on 2006-02-15
[QUOTE=MJN]:???: 
 
Interesting maths there! A string of 6 numbers, assuming you're using 0-9, has 10^6 permutations i.e. 1,000,000. Likewise, a 9-digit one would have 10^9 i.e. 1,000,000,000.
 
Mathew ;)[/QUOTE]

@MJN
Interesting.  He was actually discounting all the numbers with leading zeros, such as 000026.  While it would possibly be smart to have leading zeros, with a more secure password, it would sure make it hard to validate how many zeros you have typed in before the numbers.  You are correct with the math if you allow leading zeros, but they're a hassle to deal with.

If you wanted a six digit number with no leading zeros allowed, it would be 9 x 10^5, which is 900,000.

---

### Post by imagine on 2006-02-15
OpenSSH *is* secure. For remotely accessing a machine SSH is the way to go. But of course OpenSSH can't protect you from weak passwords or a bad configuration.

OpenSSH can be secured by itself, you don't have to use a firewall.

* If you're always accessing your Ubuntu box over SSH from the same IP-addresses, then deny access from everywhere else. Check /etc/hosts.deny and /etc/hosts.allow.
* Restrict SSH login to the actual users/groups who need to login (look up "AllowUsers" and "AllowGroups" in /etc/ssh/sshd_config). Otherwise something like this coud happen: You created a temporary test/test account for testing an application and while you were doing your tests someone used this account to login over SSH.
* If possible, use public/private key authentication and disable a password based login. Without the key file nobody will then be able to login. Enable  "PubkeyAuthentication" and disable all other "*Authentication" possibilities and UsePAM in the sshd_config.
* Disable SSH version 1 by setting "Protocol" to 2 and only 2 in the sshd_config.
* PermitRootLogin no, PermitEmptyPasswords no, Strictmodes yes or UsePrivilegeSeparation yes can be taken for granted, as long as you don't have very good reasons to change them.
* If you login remotely very rarely and at fixed times you can keep the SSH daemon disabled and start it with cron jobs when needed. sudo /etc/init.d/ssh stop && logout is a very nice way to lock yourself and everybody else out until the next cronjob ; )


[https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH)



And if really someone got access to your box: Find out how and reinstall. They could have modified every file, installed backdoors amd turned the computer into a zombie.

---

### Post by MJN on 2006-02-16
[quote=spartas]Interesting. He was actually discounting all the numbers with leading zeros, such as 000026. While it would possibly be smart to have leading zeros, with a more secure password, it would sure make it hard to validate how many zeros you have typed in before the numbers. You are correct with the math if you allow leading zeros, but they're a hassle to deal with.[/quote]
 
I ain't got a clue what you're on about there! ;) 
 
Why would having leading zeros in a password make any difference to how difficult they are to deal with?
 
As for discounting leading zeros in the original calculation, no, he just made a mistake... :)
 
Mathew

---

### Post by newuser111 on 2006-02-16
sudo aptitude install bastille

sudo aptitude install tiger

try those out, bastille is really good for locking down a system

---

### Post by Horndog on 2006-02-16
This sounds more like a browser hijack. This comes from going to questionable web sits and/or downloading infected material. If this is possible with Linux? I have no idea.

---

### Post by imagine on 2006-02-16
[QUOTE=Horndog]This sounds more like a browser hijack. This comes from going to questionable web sits and/or downloading infected material. If this is possible with Linux? I have no idea.[/QUOTE]
I do not know of any. Besides when I'm surfing the web *I* decide what's questionable, not my browser : )

But cronjobs aren't the result of browser hijacks anyway.

---

### Post by Jimmey on 2006-02-16
[QUOTE=chimera] -Change your password to something like ´ß¤&#273;>~Ç^ worked for me :mrgreen:[/QUOTE] Just like this rock I stash in my drawers keeps tigers away, all day, and all night :)

---

### Post by Horndog on 2006-02-16
[QUOTE=imagine]I do not know of any. Besides when I'm surfing the web *I* decide what's questionable, not my browser : )

But cronjobs aren't the result of browser hijacks anyway.[/QUOTE]
That's a very proud statement, but I was answering Connollyir, unless he has another identity. You should really look up what a browser hijack does. Unless you serf the web with a terminal, you and your browser are really pardners. I have seen browser hijacks happen before. The fact the the browser dials home, and the fact that OP shamefully edited that part out is another clue of were the infection came from, Bootleg software. This could be a good reason not to download "cracks."If this is not the case then, never mind about my observation.

---

### Post by Iandefor on 2006-02-16
[quote=MJN]:???: 
 
Interesting maths there! A string of 6 numbers, assuming you're using 0-9, has 10^6 permutations i.e. 1,000,000. Likewise, a 9-digit one would have 10^9 i.e. 1,000,000,000.
 
Mathew ;)[/quote]1) You're probably correct. It's been too long since I've done any probability work.

2) The system of numerology I adopted uses 1-9, not 0-9.

Therefore, 9 possible numbers to select from, not 10.

---

### Post by Connollyir on 2006-02-17
[QUOTE=Horndog]That's a very proud statement, but I was answering Connollyir, unless he has another identity. You should really look up what a browser hijack does. Unless you serf the web with a terminal, you and your browser are really pardners. I have seen browser hijacks happen before. The fact the the browser dials home, and the fact that OP shamefully edited that part out is another clue of were the infection came from, Bootleg software. This could be a good reason not to download "cracks."If this is not the case then, never mind about my observation.[/QUOTE]

Well the thing is, I really haven't done anything that would result in a browser hijacking.... my web browsing consists of this site and the wikis/howtos, government endorsed sites, university research pages and servers, etc - no place where there are sketcy goings on or even ads most of the time. My personal prognosis has since changed from a brute force attack to probably a sniffed or snooped password from my cookies or something, although he removed most of the logs that would prove it. 

I have since reinstalled, revamped, and rearmed. Im sitting behind a nice iptables configuration that has me as snug as a bug in a rug, complete with a much stronger password, and several other steps I took as recommended by the forum (thanks). 

I will be doing quite a bit more reading and I hope to get privoxy up and running for anonymity within the next week. I hope other users can see this thread and know that these kind of things do happen to Linux users, just like with Windows, and they can smarten up by taking the right precuations.

Ok my golden globe speech is done. Seriously, thanks though.

-Ian

---

### Post by paul cooke on 2006-02-17
I hide my home network behind a "hardware" firewall... "hardware" in name only cos it's really running an embedded version of Linux. The very, very first thing I did when setting it up was to change the password FROM the default of "admin" (I kid you not!!!) and ensure external remote admin was not enabled (some boxes can be admined from outside their own little network). The other thing was to find the default emergency password and change that... Some boxes have a password for remote engineers to use... they are published on the net at CIRT!!!

[http://www.cirt.net/cgi-bin/passwd.pl](http://www.cirt.net/cgi-bin/passwd.pl)

You will be shocked at how many of these little embedded Linux boxes are being run with the default passwords still in force...

People think they're safe behind their little hardware box, but in reality they're wide open if they haven't even done the basic precaution detailed in the firewall's guick setup guide.

---

### Post by skydvrgrl on 2006-02-17
I am reading this with interest as I too was hacked into thanks to a linux knowledge lapse.

I ALWAYS had my Win:doze box uber-secure, and was never "broken into" by some little script kiddie, but I was just the other day with this Ubuntu box. I am still unsure as to the correct methodology behind using firestarter to setup iptables, but I am getting there :D

What basically happened was when I used chkrootkit it came back with these results:(and I was also noticing my internet speed was a bit slower..)

Infected Ports: 1524 and 31337 (Back Orifice)
ETH1: Packet Sniffer (/sbin/dhclient3[6733])

and also to check out:
/lib/modules/2.6.12-10-386/volatile/.mounted

I really have no idea as to how serious this all makes it, but I have done a reinstall to be sure. (I am still learning *nix)

Perhaps all you other guru's out there can tell me what that all meant so I can be better prepared for next time :)

Thanks

---

### Post by kakashi on 2006-02-17
this is actually a great argument for root account enabling. 
most user (single users) set thier passwd simple. ( i use a single letter) 
so if someone figuire that out. boom. 

however enbaling root and setting a monster password on it is probably the easist thing to do.

---

### Post by kakashi on 2006-02-17
another possible security mesaure is 
1. run a ubuntu seesion in vmware player .
2. run NAT (probably iptables) and then don't forward any ports to the vmware player. 
3. run all your secure sites (maybe all... if you want to) in that. 
4. this way it'll e very hard to git into your vmware ubuntu and all you passwords should be secure
5. delete cookies everytime.

please can someone look over this method and check it. i think it should be very secure but you never know.

---

### Post by Horndog on 2006-02-17
> 

[color=red]Infected Ports: 1524 and 31337 (Back Orifice)[/color]
ETH1: Packet Sniffer (/sbin/dhclient3[6733])

and also to check out:
/lib/modules/2.6.12-10-386/volatile/.mounted


Who said Linux can't get infected?

---

### Post by K.Mandla on 2006-02-17
I've used this to generate passwords. ...

[http://www.winguides.com/security/password.php](http://www.winguides.com/security/password.php)

It keeps me from getting lazy in picking my passwords. Makes it a little tough to switch between new ones, but after a while I get used to them.

---

### Post by imagine on 2006-02-17
[QUOTE=Horndog]I have seen browser hijacks happen before.[/QUOTE]
On Linux? What browser?
Using a security hole in the browser to take full control over a system is possible but very unlikely. First you would need a flaw which allows the remote execution of arbitrary code without the user noticing it, ie by just visiting a website. In general such flaws are not very common (except for IE maybe) and the browser which the thread starter uses - Firefox - doesn't have such an unpatched hole at the moment.
And even if there is such a hole, there's still the point that the user and the programs he runs have no root privileges, ie they can't modify the system.

[QUOTE=Horndog]This could be a good reason not to download "cracks."If this is not the case then, never mind about my observation.[/QUOTE]
Of course you can infect your system by downloading and running software, be it cracks or anything else. But that got nothing to do with browser hijacking.

---

### Post by imagine on 2006-02-17
[QUOTE=kakashi]however enbaling root and setting a monster password on it is probably the easist thing to do.[/QUOTE]You also need to remove yourself from the admin group or change sudo so that it doesn't ask for your password, but for the root password.

And then the system is still more vulnerable (due to the single letter user password) than if you just let the root account disabled and used that secure password for your user account.

---

### Post by Horndog on 2006-02-17
[QUOTE=imagine]On Linux? What browser?
Using a security hole in the browser to take full control over a system is possible but very unlikely. First you would need a flaw which allows the remote execution of arbitrary code without the user noticing it, ie by just visiting a website.[color=red] In general such flaws are not very common (except for IE maybe) and the browser which the thread starter uses - Firefox - doesn't have such an unpatched hole at the moment.[/color]
And even if there is such a hole, there's still the point that the user and the programs he runs have no root privileges, ie they can't modify the system.


Of course you can infect your system by downloading and running software, be it cracks or anything else. But that got nothing to do with browser hijacking.[/QUOTE]

You think not? a quick search reveled [this]("http://ubuntuforums.org/showthread.php?t=126941&highlight=firefox+security")
How do you know what a malicious file can and will do? Maybe you can provide some proof of your claim next time. I would make you credible.

---

### Post by LordHunter317 on 2006-02-18
[QUOTE=Connollyir]I just spent the better part of an hour trying to figure out why Konqueror was randomly launching and dirrecting me to a warez site. I am relatively new to Linux, but it was my understanding that spyware and viruses are infrequent at best - which meant this was a directed and personal attack on my machine.[/quote]No, it doesn't.  Almost zero, attacks against anyone anywhere are manual anymore.

> Eventually a friend and I found the cron job that was responsible for the poppups and got rid of them. 

Password has since been changed and now I am much more motivated to put together the firewall box I've been putting off for some time.

Pretty shady stuff eh?Instead of doing that, you should be reinstalling this box, like yesterday.

[quote=mstlyevil]I would suggest you install and run Firestarter until you can get your hardware firewall up and running.[/quote]There's no need to do that unless you're running servers.  Recommending a firewall as an instant response to an intrusion is silly, unless we know what the vector is.

[quote=Virogenesis]If you do decide to use ssh use something like port knocking to stealth the port.[/quote]Port knocking adds zero security. Don't bother with it.  Setup a proper firewall if you need to run a server application.  IF you don't know how, ask.  Don't go through obscuring methods that don't actually add any access control.

[quote=TechSonic]
I use a password that uses this format. 84LKDIuu84gfufYWEnv8723UM20EWBAbal5eal but not exactly in that order but Thats how long I use. Or until the password box says I can't put anymore in. Then I print the password and stick it to the bottom of my keyboard.[/quote]Password length is almost irrelevant except for dealing with rainbow table attacks.  On Linux, that's presently irrelevant as hashed passwords are used.

Sticking it to your keyboard just wrecks your physical security.  If you can't train yourself to remember it or remember it naturally, it's a bad password.

[quote=Bandit]I dont think it would be. Of course the more characters the better.[/quote]No, that's not true.

> Thanks to cookies, most users dont know what cookies they let enabled. Cookies are great for reporting keystrokes back to another computer.No, they're not.  How can data sent to you from another computer, **that you simply send back, *unmodified***, be used for reporting keystrokes.

Do you even know what a cookie is?

> This is why firewalls are a must with todays computers.Firewalls don't stop keyscanners.  I have several in my present possesion a firewall cannot stop.

[quote=GeneralZod]I always use public key authentication for SSH, but I see no one here has suggested it. Is it a bad move?[/quote]No, where it can be used, it's a brillant idea.  It's only flaw is you cannot enforce policy on it, so it's not idea for a group of users you don't trust.

[quote=snowjunkie]Are you serious? How long does it take you to log in? 2.5 hours?[/quote]My root password on most of my systems (Linux, Windows) is 21-ish characters and I can type in it 3 seconds.  My SSH keypair passphrases are 25 or longer.

[quote=imagine]* PermitRootLogin no, PermitEmptyPasswords no, Strictmodes yes or UsePrivilegeSeparation yes can be taken for granted, as long as you don't have very good reasons to change them.[/quote]***No, they CANNOT be taken for granted.***  They're integral to SSH security.  IF you don't know what something does, it doesn't mean you can take it for granted.

[quote=kakashi]
however enbaling root and setting a monster password on it is probably the easist thing to do.[/quote]No, it isn't, seeing as most compromises don't occur from a disclosed password at all. 

[quote=imagine]On Linux? What browser?[/quote]Firefox, which is quite the security nightmare.

> sing a security hole in the browser to take full control over a system is possible but very unlikely.It's trivial if it's running as root.  Assuming that's not the case, then it's impossible due to a flaw in the browser (other components, like the kernel, notwithstanding).

> First you would need a flaw which allows the remote execution of arbitrary code without the user noticing it, ie by just visiting a website.Such have existed in Firefox.

> In general such flaws are not very common (except for IE maybe) and the browser which the thread starter uses - Firefox - doesn't have such an unpatched hole at the moment.That's not a known quantity and I have no longer any trust in the mozilla team to really believe there isn't.

---

### Post by imagine on 2006-02-18
[QUOTE=Horndog]You think not? a quick search reveled [this]("http://ubuntuforums.org/showthread.php?t=126941&highlight=firefox+security")[/QUOTE]You're right, in the latest Firefox version for Breezy (1.0.7-0ubuntu20), there is one unpatched hole, because the developers didn't backport the fix yet and obviously do not want to update Firefox to 1.5.0.1 in Breezy. This is an example of the "no-upgrade" policy taken too far IMHO.


[QUOTE=Horndog]How do you know what a malicious file can and will do? Maybe you can provide some proof of your claim next time. I would make you credible.[/QUOTE]A program can do everything what the user who started it can. That usually doesn't include modifying the system, unless you run everything as root.

---

### Post by imagine on 2006-02-18
[QUOTE=LordHunter317]No, they CANNOT be taken for granted. They're integral to SSH security.  IF you don't know what something does, it doesn't mean you can take it for granted.[/QUOTE]Erm maybe I used the wrong words here. What I wanted to say is that those options shouldn't be changed.
And yes I do know what those options mean, everybody can look them up in the man-page.

[QUOTE=LordHunter317][QUOTE=imagine][QUOTE=Horndog]I have seen browser hijacks happen before.[/QUOTE]On Linux? What browser?[/QUOTE]Firefox, which is quite the security nightmare.[/QUOTE]
Can you give more details about the hijacking? I know that Firefox is not exactly the most secure browser, probably because the idea to use web-technologies to draw the GUI was not the best idea from a security point of view. But I didn't see any hijacked Firefox browsers on Linux-platforms yet though.


[QUOTE=LordHunter317]It's trivial if it's running as root.  Assuming that's not the case, then it's impossible due to a flaw in the browser (other components, like the kernel, notwithstanding).[/QUOTE]I hope the thread starter didn't run his browser with root privileges...

---

### Post by LordHunter317 on 2006-02-18
[QUOTE=imagine]Can you give more details about the hijacking?[/quote][http://secunia.com/advisories/18700/](http://secunia.com/advisories/18700/) See issue 3.

[http://secunia.com/advisories/16869/](http://secunia.com/advisories/16869/) That one is Linux specific.

Both have published, working exploits.  Obviously, if he was running 1.0.7, then  he wasn't exploited by either.  But firefox has been a compromise path a few times, and that's only two issues.

> But I didn't see any hijacked Firefox browsers on Linux-platforms yet though.Not only can most of the hijacked code vulnerabilites run on Linux, as I noted, there are several Linux specific ones.  Oops.


> I hope the thread starter didn't run his browser with root privileges...Unless the cronjob was running as root (he didn't say), then you don't need root to insert a cronjob running as yourself.

---

### Post by Connollyir on 2006-02-18
[QUOTE=imagine]I hope the thread starter didn't run his browser with root privileges...[/QUOTE]

No root privs, cronjob either I think - but that was a couple days ago and I don't really remember the specifics. Konqueror was never run as root while I was using it though.


-Ian

---

### Post by chajuram on 2006-02-18
[QUOTE=TechSonic]I use a password that uses this format.  84LKDIuu84gfufYWEnv8723UM20EWBAbal5eal  but not exactly in that order but Thats how long I use.  Or until the password box says I can't put anymore in.  Then I print the password and stick it to the bottom of my keyboard.


I've never had my security broken, not ever.[/QUOTE]

I admire you!!

---

### Post by nzruss on 2006-02-20
Will being behind a NAT router reduce the chances of this happening? - (a NAT router is not supposed to respond to traffic that was not solicited.) 

I also went to GRC.com and did a sheilds up check on my Unbuntu install once i'd installed it, and it showed no open ports. I thought it Unbuntu had a default firewall or something.

---

