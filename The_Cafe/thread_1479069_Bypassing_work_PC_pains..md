---
title: "Bypassing work PC pains."
date: 2010-05-10
forum: The Cafe
---

### Post by Shakz on 2010-05-10
Hey all. I hope this does not go in support but I am sure the solution is easy enough. 

My pops hates his work PC because its dog slow and the "network weenies" Block all the email sites etc (at the PC level because outside of the work Network they are still blocked) I could prolly hack it but I would rather not. I dont jack with my work laptop because its not mine....like that one isnt his so I dont feel right about hacking the hosts file or whatever they are doing to block him. Besides its a law enforcement laptop so....I just dont wanna go there. 

I am putting his home PC on linux anyway prolly this weekend. I was thinking though. Wouldnt it be cool to just give him a thumb drive he could boot up on. 

He was interested in getting a personal laptop for when he goes out of town so he can email my mom or use skype or fart around on the net. Work laptop blocks all that. So I was thinking hey he can just boot up on ubuntu. He is a cop though and makes diddly squat for pay. $400 bucks is a huge chunk of change for him.....hell for anyone really. Point is he is boning up for retirement and cant afford to spend the money on what he considers a luxury.

Problem: Settings dont change when saving files even on USB drive. I ran a proof of concept test on a 1gb thumbdrive on my (already loaded with Karmic) laptop. Its got an nvidia card and bwm wireless...both of which take proprietary drivers. I loaded them but the system didnt seem to save the settings after a reboot. Do I just need to create a new user? How can I make it so my pops has a little 16gb thumdrive that he can plug into his work laptop and make it his own for just a little while. 

If yall know of a good wiki on how to do this with Ubuntu I would appreciate it. 
Thanks in advance!
Shakz

---

### Post by undecim on 2010-05-10
Use System -> Administration -> Startup Disk Creator, and make sure you give it the maximum space to saving settings.

---

### Post by Paqman on 2010-05-10
You can either use the USB Startup Disk Creator to make a persistent Live USB, or you can just install the regular system directly onto a USB stick.

---

### Post by Mark Phelps on 2010-05-10
> **Shakz said:**
> ... Besides its a law enforcement laptop so....I just dont wanna go there...

I'm not really clear on what you're intending to do, but I work in a closely allied part of the industry and, in our situation, doing ANYTHING to the program-provided laptop is grounds for prosecution and termination. Period.

They regularly monitor the activities of the machines, internet usage especially, and something as "innocent" as checking your personal webmail will get you a reprimand -- and if you keep it up, prosecuted and fired.

So, as long as you're not touching his work laptop in any way -- including setting it up to boot from  USB, then you (actually HE) are safe.  But if it's your intent to touch his work PC, strongly suggest he check with his employer first.  

Hey -- I'm not advocating this kind of draconian rule, I'm just saying that the "powers that be" have made it a condition of employment (we have to sign a notarized statement agreeing to the terms). 

Would hate for your dad to lose his job (or worse!) simply so you guys can experiment with Linux.

---

### Post by KiwiNZ on 2010-05-10
Closing this . Refer Code of conduct

---

