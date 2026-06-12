---
title: "laptop security - protecting BIOS w/ password"
date: 2008-10-01
forum: Security
---

### Post by adamogardner on 2008-10-01
Hi so I want to take some precautions as described in this article: [http://conigs.com/static/misc/laptop.html](http://conigs.com/static/misc/laptop.html)  If anyone has a better article I'd like to read it.  He says I should lock the BIOS to prevent the thief from wiping the hard drive.  How is this done?

---

### Post by cariboo on 2008-10-01
Passwording the bios will only keep the average thief out, anybody that knows anything about computers can clear the bios password in less than 5 minutes. If you feel better putting a password on your bios, when you laptop is first starting it should tell what key to press to enter the bios, I have an HP and if I remember correctly I have to press F10 to enter the bios. Once your are in the bios there should be a menu, usually you use the arrow keys to move around and Pgup and PgDn to change a value.

Jim

---

### Post by adamogardner on 2008-10-01
> **cariboo907 said:**
> Passwording the bios will only keep the average thief out, anybody that knows anything about computers can clear the bios password in less than 5 minutes. If you feel better putting a password on your bios, when you laptop is first starting it should tell what key to press to enter the bios, I have an HP and if I remember correctly I have to press F10 to enter the bios. Once your are in the bios there should be a menu, usually you use the arrow keys to move around and Pgup and PgDn to change a value.

Jim

Oh I see.  So HP (my computer) will have instruction for this, it's not relevent to Ubuntu.

---

### Post by cariboo on 2008-10-02
No it happens before any OS is loaded. Have a look at this:

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

for an explanation of what the bios is.

Jim

---

### Post by hyper_ch on 2008-10-02
bios password will not prevent anyone from wiping your harddisk or copying info from it.

---

### Post by jerome1232 on 2008-10-02
Even if the BIOS password couldn't be over ridden (which it's very easy todo) he would just take the hard disk out and hook it up to another machine.


I'd be more worried about him copying your data (full disk encryption anyone), the data doesn't do you much good sitting at the thiefs house anyways.

---

### Post by niteshifter on 2008-10-02
Hi,

I agree - setting the BIOS power up password will not protect the data on the hard drive. It provides DOS (Denial of Service, in this case usage) protection. If somebody else sets the password, then you are denied use of the machine. It also provides a form of data protection: easy enough to boot from a Live CD and plant some illegal / embarassing material in the file system. And no, whole disk encryption isn't your salvation (/boot isn't encrypted).

Yes, I know this protection measure is easily hacked. If you can access the internet and search for the means to do so and deploy the tool upon the machine, that is. Before you say "I can always get access" think about that carefully: Can you really? When traveling? Even with net access can you deploy the tool you found? Sure your machine will boot from USB? Got a floppy drive?

It's easiest to hack a machine without a BIOS password set. Why make it easy for the attacker (or practical joker)? Set the password, it provides another layer in whatever security scheme you choose to use and costs you nothing, or a at most a bit of functionality: When I set the BIOS password on this machine, suspend died - but hibernate still works. I am willing to trade a few seconds of time for the extra security, but as always YMMV.

---

### Post by hyper_ch on 2008-10-03
and what's so bad about unencrypted /boot?

---

### Post by niteshifter on 2008-10-03
> **hyper_ch said:**
> and what's so bad about unencrypted /boot?

It's where I - as malevolent attacker - can place an incriminating / embarrassing file via booting the unsecured machine with a CD or USB drive, leaving the victim to explain it's presence.

---

### Post by hyper_ch on 2008-10-03
yeah, just how convincable would it be to have 1 incrimination file in /boot while the rest of your OS is totally encrypted...

---

### Post by jerome1232 on 2008-10-03
> **niteshifter said:**
> It's where I - as malevolent attacker - can place an incriminating / embarrassing file via booting the unsecured machine with a CD or USB drive, leaving the victim to explain it's presence.

I think he's being sarcastic :)

---

### Post by nubdora on 2008-10-03
A better security precaution would be a) don't allow manual access to your machine by others. If that's not possible, b) don't put any thing on said machine you wouldn't want others to  see/access/etc. The latter is always your safest bet when you aren't using your "precious". My "precious" is always in one spot under lock and key.

---

### Post by niteshifter on 2008-10-03
Hi,

Actually, I was being serious - and thinking outside the box.

My pretend victim in this scenario thinks of themselves as smart, savvy. The company he works for provides him with computation resources and network access. Being smart and savvy he knows better than to use the corporation supplied resources - he brings his own laptop to work, uses it for email and whatnot and connects to the Internet via cell phone.

I boot his personal laptop via CD while he's running some errand. Create a text file containing (pick one):
A) A death threat 
B) A request for sexual favors from a coworker or another.
C) A plan to extort money from someone.
... and there can be more. Not much text is needed, 1KB is about a half a page. I'd probably have many times that much space. This file is produced to appear as a private 'note to self' style of text.

I then employ some "social engineering" - I plant the rumor that I saw my victim working on some file, the content was "disturbing". I keep at it.

Soon enough the victim will be confronted by management. Sooner if I grease the skids by spoofing his company email and aggravate some fractious relationship he has with a coworker. Victim ponies up the laptop - they have to, they're boxed in: refuse to produce it for examination they may as well admit guilt.

Now pause for a moment and look what I've accomplished: at the very least I've painted the victim as a problem in the eyes of management. I've put his job at risk, because what he appears to have done contravenes company policy. Possibly cost him the job, possibly got him crosswise with the Law. I have succeeded at damaging him. With a bit of luck, I got him in enough  hot water to force him to retain an attorney, costing him money.

Think the above can't happen? Never been a victim of vicious gossip in school? Or at work? Never saw someone who was? Of course it happens. The "hack" employed above is with human psychology, the planted file also plays on that by providing a tangible, physical item for people to see - after all seeing is believing ....

The above scenario I detailed was derived from real world experience. It wasn't a file in /boot - it was a fellow coworker that believed in the crappy encryption Word Perfect offered. Someone employed a cracker tool and edited some of his files. Rather than deal with it management took the easy way out: they fired him (the victim).

Good security requires thinking outside the box. It requires multiple defensive mechanisms. Setting the BIOS password is just an easy step, with low cost. Why not do it? We can't retain physical possession 100% of the time.

Final note: My posts in this section are frequently lengthy, like this one. The purpose is to jog minds. For good reason: some here are victims of an all to common fallacy: I"m smart -er, -est, the attacker isn't. 

Problem: That isn't always true.

---

### Post by hyper_ch on 2008-10-03
still not convincing... if someone encrypts his whole system and then puts a file in boot.. it's just not convincing.

---

### Post by jerome1232 on 2008-10-03
And the bios password wouldn't stop anyone from putting a file there anyways.

All you have to do is move a jumper on the motherboard over one pin for a few seconds, then move it back. cmos gets flashed, bios is back at factory default settings. 

I haven't heard of a board that you can't flash the cmos on.

---

### Post by volkswagner on 2008-10-06
> **jerome1232 said:**
> And the bios password wouldn't stop anyone from putting a file there anyways.

All you have to do is move a jumper on the motherboard over one pin for a few seconds, then move it back. cmos gets flashed, bios is back at factory default settings. 

I haven't heard of a board that you can't flash the cmos on.

One word, Thinkpad.  Many IBM Thinkpad laptops have a prom.  The prom contains the bios admin password.  I have seen a solder on hack with a serial cable and software to crack it.  Yes it can be done, with risk to bricking the unit.

I only know this because, I just purchased a bunch of Thinkpads.  Two of the units (Thinkpad A31), have bios protected passwords.  I can't even get into allow boot options.

Here is the solution I found.  yet I have not easily found the chip.

[http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/]("http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/")

---

### Post by jerome1232 on 2008-10-06
So thinkpads come with with a supervisor password that's unique to each individual machine. And from what I can see shorting jumpers doesn't deactivate this because it's a default setting, out of the factory.

I now want to get a thinkpad just to see :)

Wow these things actually have a little bios level security it seems, if your only interest is obtaining data stored on the laptop you can still take the hard disk out and hook it up to another machine though.

Apparently encryption has one weakness too, ram actually does retain data for several seconds to several minutes after power down at room temp. It's possible to retrieve the key from the ram of a machine that was just turned off.

---

### Post by hyper_ch on 2008-10-07
> **jerome1232 said:**
> Apparently encryption has one weakness too, ram actually does retain data for several seconds to several minutes after power down at room temp. It's possible to retrieve the key from the ram of a machine that was just turned off.

It must store the key somewhere and the more you cool down the ram the longer it will be retained. As the study has shown, older ram retains the data longer than newer one and it also assumes, the attacker must now that all data is encrypted. If he's not prepared he won't get the key from ram.

---

### Post by jerome1232 on 2008-10-07
> **hyper_ch said:**
> It must store the key somewhere and the more you cool down the ram the longer it will be retained. As the study has shown, older ram retains the data longer than newer one and it also assumes, the attacker must now that all data is encrypted. If he's not prepared he won't get the key from ram.

By older do you mean because of age, the longer the ram stick has been in use the longer it will retain data, or has the manufacturing of ram improved, and these newer, better sticks don't retain data as long.

Are there any encryption methods that you know of that don't as of now store the key in ram.

---

### Post by hyper_ch on 2008-10-07
There are some drives that have encryption keys in the disk controller... don't ask me how that works... however for the cold boot attack, here's the published paper:

[http://citp.princeton.edu/pub/coldboot.pdf](http://citp.princeton.edu/pub/coldboot.pdf)

---

### Post by volkswagner on 2008-10-07
> **jerome1232 said:**
> So thinkpads come with with a supervisor password that's unique to each individual machine. And from what I can see shorting jumpers doesn't deactivate this because it's a default setting, out of the factory.

I now want to get a thinkpad just to see :)

Wow these things actually have a little bios level security it seems, if your only interest is obtaining data stored on the laptop you can still take the hard disk out and hook it up to another machine though.

Apparently encryption has one weakness too, ram actually does retain data for several seconds to several minutes after power down at room temp. It's possible to retrieve the key from the ram of a machine that was just turned off.

The user/Admin enables and sets the password from within the BIOS (not the factory).  The data is written to the prom.

---

