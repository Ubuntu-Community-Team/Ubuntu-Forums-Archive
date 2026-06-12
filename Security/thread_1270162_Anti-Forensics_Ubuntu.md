---
title: "Anti-Forensics Ubuntu"
date: 2009-09-19
forum: Security
---

### Post by m1k3l3 on 2009-09-19
Hello everyone, 

 I am building an anti-forensics distro Ubuntu-based  (thesis university, not terrorism :-)). 

 Currently I have implemented: 
 [Wiping] Secure-delete (I created an interface to simplify use) 
 [Encryption] True-crypt 
 [Virtualization] Virtual-box 
 [Network Security] Tor / firefox 
 [Steganography] Steg-Hide / SteGUI 

 To implement (such as software can I use?): 
 [Data Hiding] Filesystem Insertion? 
 [Create false evidence] Modified Timestamp file? 
 [Create false evidence] md5 collision? 
 [Network Anonymity] Attacks on wireless networks (air-crack?) 
 [Mail Encryption] NewPGP / Thunderbird? (Is a good choise?)
 [Firewall] IPtable changes (how?) 
 [Antivirus] Really needed? 

 other suggestions for this project?

 Thanks to all those who want to help me

---

### Post by fbnaia on 2009-09-20
Hi, very interesting subject...

At **[irongeek's website]("http://www.irongeek.com/")** you can find a presentation he did on **[B][Anti-forensics]("http://www.irongeek.com/i.php?page=videos/anti-forensics-occult-computing")**[/B]

Theres the **[Metasploit Anti-forensic project]("http://www.metasploit.com/research/projects/antiforensics/")**, although not updated recently...

As for other suggestions, it depends on what actually you want to achieve, if it's going to be a live-distro that leaves no traces like **[anonym-os]("http://sourceforge.net/projects/anonym-os/")**, then you would need to make sure that the live cd doesn't leave any "traces" behind or makes other changes to the computer that could be tracable. Also, instead of just using tor for firefox, you could try something like **[B][JanusVm]("http://www.janusvm.com/")**[/B] for the whole system.

---

### Post by m1k3l3 on 2009-09-20
The aim of this project is not primarily a live, but a system installed, to test the effectiveness of forensic tools (CAINE) against my antiforensics distro(AFUBUNTU). 

 The anonymity software is to complete the work of a antiforensics distro, but isn't the main goal.

---

### Post by fbnaia on 2009-09-20
So you will be testing specific tools and methods, not the whole system itself right?. Either way, come over to the **[Forensic Focus Forums]("http://www.forensicfocus.com/computer-forensics-forums")**, you can get more related information there.

---

### Post by i.r.id10t on 2009-09-20
> **m1k3l3 said:**
> 

 The anonymity software is to complete the work of a antiforensics distro, but isn't the main goal.

Working from a livecd, perhaps with something like sshfs for persistent data to a truster server/site (VPS in a different country, etc), or not use persistent data at all (if it is never stored, it can never be recovered).

Just for giggles, read Little Brother (free online at craphound.com Cory Doctorow at [http://craphound.com/littlebrother/](http://craphound.com/littlebrother/) ) for some other ideas.

---

### Post by solitaire on 2009-09-20
i've been toying with an idea to move all temp files created by an OS and applications to an encrypted /tmp partition (it will use a single use encryption key that's forgotten apon shutdown) 

Then the /tmp partition and folder structures are recreated during boot (the same way an encrypted swap partition is created in secure boots) so that there is NO recoverable temp data for any program.

The weakest link in ANY machine / laptop security is the user.
If he gives up his password then even the most secure system can be examined.
If he does not had the key to start with it's more secure... ^__^

---

