---
title: "Possible boot sector virus"
date: 2011-09-14
forum: Security
---

### Post by Sc0urgeTR on 2011-09-14
Hello all! I wish my first forum post was of a more enjoyable matter but I am in over my head,

Recently I've switched over to Ubuntu trying to get away from a plague of attacks aimed at diabling me from using windows. I thought well why not use a system not so easy to pull apart... linux... a system for noobs.. Ubuntu! so here I am with Ubuntu now 

I have two problems. I get ping fluctuations when pinging my router and if I try and game online I recieve ping over 4000ms. If I try to burn disks my DVD burner will burn tiny little whols into the disk making it corrupted.

If I format my hard drive it goes back to normal but after a couple of boots back into Linux it will go back to fluctuating ping and the inability to burn anything to disk.

I've flashed my bios just incase it was bios level exploitation but I don't think it is, I think its boot sector level. I'm really not sure how to get rid of a boot sector virus that can hang around after a full format.

(back story: while running windows the symptoms were much worse, I could run windows 7 with out any problems but if I updated a few hours later remote connection would be enabled from a disabled state, the whole network would go down (bunch of pcs all unable to connect to the router) the network would go up again everyone can connect to it except me. 

Diagnose the adapters and it would say could not bind protocol stack to the adapter. Couldn't boot in safe mode, the system restore would be unuseable. the audio drivers would point to the wrong drivers and the network card couldn't get have the protocol stack assigned to them)

it seems as if it's the same virus but because i'm now using linux it can't attack the computer the same way,

any ideas? XD
could it be something else?
I'm running from a fresh install with nothing else on it at the moment and it's ping is jumping around a lot already.

---

### Post by cariboo on 2011-09-15
This isn't to say that it couldn't be a virus, but the chances are slim to none. It sounds more like a hardware problem. Have you checked the hard drive using the hard drive manufacturers testing utilities, and swapped the network card for a known good one? If you still have the same problems, I'd suggest a motherboard problem.

---

### Post by Dangertux on 2011-09-15
In my opinion you have a failing network card and dvd+-rw drive.

The reason I don't think you are correct in your assumption that it was bios or boot-sector level malware is this.

bios level malware re-infects at kernel load time by passing ACPI arguments to the kernel (usually). In this case if it was acquired on Windows it would be unlikely to be able to pass said information to the Linux kernel.

The amount of code actually stored in the boot-sector is simply enough to reinfect the machine
by causing it to "egg-hunt"  or go get the rest of it's code from elsewhere. Even IF it could do this, the code downloaded would likely be for Windows, thus not running correctly on Linux.

It just makes more sense that you have failing hardware than the world's first multi-platform persistant malware. The simplest solution is most often the correct one.

---

### Post by Sc0urgeTR on 2011-09-15
I see and I agree with you angle on this view but the reason why I question that it's just hardware is that it caused a network wide failure to connect to the router on serveral occassions. ALL computers couldn't connect to the router. Then the router reestablishes networking.

If it's hardware related it's the router, the dvd player the cd player, the mobo. everything all at once and it's affecting multiple computers. But all the other computers function fine after the router reestablishes connectivity EXCEPT mine.

I only had isues with my hardware when I used microsoft update.

The event viewer suggests that remote connect was used.

System restore points are deleted except for the one where the microsoft update is.

It just seems like multiple angles of attack. 

It would be odd for it to run fine for a 8 months then just have everything on the system fail.

Let me be more specific. the Windows drivers for the audio after a windows update would say that the high def drivers are the drivers for the digital drivers. You can't play LAN games because it gets sporadic over 1000 ping and you'd get sporadic CPU spikes. YOU can't use safe mode in windows it shows NO options. all the system restore points are deleted. the REMOTE connection has been used even though it's deliberately turned off. 

I just used the wifi card on my mates computer and it functions normally over a 16 hour period.

I need to test the hard drive on another computer.

Guess then i need to shove the mobo into another computer to. I don't have access to another computer so testing hardware is gonna be annoying.

All I can think of is that if it were boot sector, hardware kernels can be applied to both the linux and the Windows OS because they use similar drivers. I've never seen or heard of this but it seems more complex than a hardware issue for it to affect multiple computers. 

But I'm certainly going to take your advice and start testing my hardware. Despite the fact Windows said EVERYTHING was normal even though half the devices couldn't function properly. THat just doesn't ever happen in windows if somethings wrong it says it's wrong I've never had false-positives for hardware functionality in Windows.

---

### Post by Sc0urgeTR on 2011-09-15
Oh and with the egg hunt thing to do with bios level. You are right but I think it was being remotely connected else where to get the rest of the data to make everything stuffed again. I have been wondering wether it's a new way WAT connects to a computer with illigitimate versions of windows to disable hardware via remote assistance.(yeah i'm a pirate cause I'm poor if you've got a problem with it take it up with my imaginary highly qualified legal team) Anyway can't prove anything other than there was a weird network connection happening during the time of the attack and there was still network data flowing a little bit when the whole of the network was down. well guess i'll have to wait a week to start testing computer parts in my class room blah. I'm an I.T student and I can't even test my own hardware for faults because I'm to poor to have another computer to test with XD @shakes fist at computer@ can someone code me a program that can connect to a banks server to falsify financial records and boost my account a couple of k? hihi

Thanks for your input guys it's helped me keep a little bit of focus when I just wanna chuck my computer.

---

