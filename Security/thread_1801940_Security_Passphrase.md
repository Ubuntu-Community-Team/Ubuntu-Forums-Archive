---
title: "Security Passphrase"
date: 2011-07-11
forum: Security
---

### Post by edmund085 on 2011-07-11
I have a security passphrase on my documents, but htere is a big heap of problem, The Ubuntu OS is originally installed on my other CPU which means a different motherboard, So I decided to moved it to another CPU with a different motherboard since the old CPU power supply just got blown, the problem is that, the operating system wont work, and I need those files in my windows OS, but i cant access my files because its encrypted even if im using DiskInternals Viewer. How can I get back my files?

---

### Post by bodhi.zazen on 2011-07-11
> **edmund085 said:**
> I have a security passphrase on my documents, but htere is a big heap of problem, The Ubuntu OS is originally installed on my other CPU which means a different motherboard, So I decided to moved it to another CPU with a different motherboard since the old CPU power supply just got blown, the problem is that, the operating system wont work, and I need those files in my windows OS, but i cant access my files because its encrypted even if im using DiskInternals Viewer. How can I get back my files?

How did you encrypt your files ? With Windows ? If so, you will have to use the windows tools to decrypt them.

As this seems to be a Windows problem, I suggest you use a windows forums or contact Microsoft.

---

### Post by edmund085 on 2011-07-11
locking the first thread was rude since i didnt say "thank you! you solved my problem", since the admin totally misunderstood the whole scenario or the situation, i will have to repost. I didnt encrypt it with windows, I encrypt it using the ubuntu since i put a passphrase on my account, I switch motherboards and the ubuntu OS wont work or boot, so I need to get those files from ubuntu to windows. Since I'm new to ubuntu I dont know how to fix or repair the problematic Ubuntu OS. 

So what I did is i used the other operating system installed in my 2nd hard drive which is windows, I used a specific viewer to view those files from ubuntu hard drive, but sadly those files were enrypted and I dont have an idea how to decrypt it. 

The only solution I want, is how do I get those files out from the Ubuntu to windows, or how do i get it. Or do you have any alternative solutions so that i can still access those files by either repairing the ubuntu OS and how to do it, or using something to access it.

---

### Post by haqking on 2011-07-11
> **edmund085 said:**
> locking the first thread was rude since i didnt say "thank you! you solved my problem", since the admin totally misunderstood the whole scenario or the situation, i will have to repost. I didnt encrypt it with windows, I encrypt it using the ubuntu since i put a passphrase on my account, I switch motherboards and the ubuntu OS wont work or boot, so I need to get those files from ubuntu to windows. Since I'm new to ubuntu I dont know how to fix or repair the problematic Ubuntu OS. 

So what I did is i used the other operating system installed in my 2nd hard drive which is windows, I used a specific viewer to view those files from ubuntu hard drive, but sadly those files were enrypted and I dont have an idea how to decrypt it. 

The only solution I want, is how do I get those files out from the Ubuntu to windows, or how do i get it. Or do you have any alternative solutions so that i can still access those files by either repairing the ubuntu OS and how to do it, or using something to access it.


so to be clear.

You ecnrypted your windows drive whilst using Ubuntu ?

So what did you use to encrypt it ? Truecrypt ?

and do you remember the passphrase used ?

---

### Post by edmund085 on 2011-07-11
ill be very clear.... 1. I didnt encrypt it with Windows or any other program. The files were encrypted by UBUNTU. BY UBUNTU! BY UBUNTU!. As I browse my files using Windows OS specifically DIskInternals software that lets me view the inside of the linux drive. All i see is enrypted and passphrase. I want those files out of that drive and either place it in a flashdisk or in the windows, or any other alternative solutions, as long as i get my files out of there an place it in a new storage. 

And sadly I forgot my passphrase... either i misplaced it or i lost it, i dont know where to find it....

---

### Post by edmund085 on 2011-07-11
i just found the passphrase, which is very long. Can I ask if there's any way I could make my own passphrase that I could remember?

---

### Post by edmund085 on 2011-07-11
i just found the passphrase but still i dont know how to open those encrypted files.

---

### Post by squenson on 2011-07-11
Sorry but I hope that there is no solution to your problem as it would mean that any encrypted disk can be easily decrypted without the password...

Edit: apparently, you have the passphrase so what is the error message you get when you try accessing the encrypted files?

---

### Post by CharlesA on 2011-07-11
> **edmund085 said:**
> locking the first thread was rude since i didnt say "thank you! you solved my problem", since the admin totally misunderstood the whole scenario or the situation, i will have to repost.

I have merged the new thread with the old thread and reopened it.

If you've got a problem with the decision of a mod or admin, create a thread in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123").

Also note: Bumping threads before 24 hours has passed is frowned upon.


Anyway, you still haven't said what you used to encrypt the files. Did you do it at install or afterwords?

---

### Post by bodhi.zazen on 2011-07-11
> **edmund085 said:**
> ill be very clear.... 1. I didnt encrypt it with Windows or any other program. The files were encrypted by UBUNTU. BY UBUNTU! BY UBUNTU!. As I browse my files using Windows OS specifically DIskInternals software that lets me view the inside of the linux drive. All i see is enrypted and passphrase. I want those files out of that drive and either place it in a flashdisk or in the windows, or any other alternative solutions, as long as i get my files out of there an place it in a new storage. 

And sadly I forgot my passphrase... either i misplaced it or i lost it, i dont know where to find it....

If you need assistance you will need to learn to communicate better.

What does changing your mother board have to do with your problem ? What is "DIskInternals software" ?? I can not even tell what files you are trying to access, files on your window partition or your ubuntu partition ?

The bottom line , however, is if you encrypted a file , files, and you lost your paraphrase, you are out of luck.

 If you somehow remembered your passphrase, and want to change it, you need to either read the documentation or tell us what you are using for encryption. Truccrypt ? Luks ? gpg ?

Slow down and try to make a coherent post ;)

---

### Post by Bachstelze on 2011-07-11
From what I understand:

edmund085 encrypted his home directory in Ubuntu during installation (so with ecryptfs),

the Ubuntu system is broken, apparently from a hardware problem,

edmund085 is using a Windows program to access his Ubuntu files, but the program obviously chokes on the encrypted files.

So edmund085 now wants to know how to access his files.

If what I said above is correct, recovering the files can be done from a Live CD, following instructions from the Wiki : [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

---

### Post by edmund085 on 2011-07-11
I have 2 CPU's and Ubuntu was installed on the newer CPU, the power supply of the newer CPU broke, so I have to use the OLD CPU which has an old Power supply and the thing is it does not support the new motherboard, so I have to use the old motherboard. After switching to the old CPU, the Ubuntu OS in the 2nd Hard Drive didnt work, I only get a dark screen in the startup, so I decided to install Windows on another hard drive so that I could maybe get my files in the Ubuntu so that I can reformat the Ubuntu Drive and make a new installation. But sadly, When I used DiskInternals(A software that can browse a linux drive using windows, since the format of the drive is different and cannot be accessed by a windows explorer) and find my Documents, all I see is encrypted files, then I remembered that I encrypt my account, or placed a passphrase in order to encrypt it. Tha'ts my problem, I just want to get my files, cause it has family pictures, and my fathers business documents especially important spreadsheets. 

@squenson: Wouldnt you cry for help if your important files that contains important family pictures, business spreadsheets and documents, especially music that you have bought using i tunes, and family videos, just got encrypted and the Operating System you use had a problem? Shouldn't you be worried about that? I hope also this happens to you, so that you will know how it feels to be worried and be frustrated at the same time.

@bodhi.zazen: sorry, I was just furious last night maybe because of the frustration and all the worries especially the pressure coming from your mother and your family which is telling you and scolding you because you broke the power supply. I just need to calm down in order for others to understand my problem better... peace.. :)

@[Bachstelze]("http://ubuntuforums.org/member.php?u=51114"): thanks that you have understand my problem, i will try your link given below. But please dont close the thread first, cause I am new to Ubuntu and maybe I will post if something comes up or a problem arise. About the Live CD, I am using a flash disk in order to make the installation, is it desame?

---

### Post by Bachstelze on 2011-07-11
> **edmund085 said:**
> About the Live CD, I am using a flash disk in order to make the installation, is it desame?

Yes.

---

### Post by edmund085 on 2011-07-12
another thing... since i am using the old model of my cpu, it is slow and it cannot support ubuntu 10 because it wont meet the requirements, so I am looking for ubuntu 8 which will meet the requirements but the problem is I cant find the download link and all i see is a documentation. And my follow up question is that, can I still proceed with the link you have given, if Im using a Live CD with a different version from the one installed on the hard drive?

---

### Post by Bachstelze on 2011-07-12
> **edmund085 said:**
> And my follow up question is that, can I still proceed with the link you have given, if Im using a Live CD with a different version from the one installed on the hard drive?

No, or at least certainly not with a 8.* version.

---

### Post by westie457 on 2011-07-12
> **edmund085 said:**
> another thing... since i am using the old model of my cpu, it is slow and it cannot support ubuntu 10 because it wont meet the requirements, so I am looking for ubuntu 8 which will meet the requirements but the problem is I cant find the download link and all i see is a documentation. And my follow up question is that, can I still proceed with the link you have given, if Im using a Live CD with a different version from the one installed on the hard drive?

Hello, I realise this answer will have no commands to run in a terminal or use any os until these suggestions are implemented.

From my understanding of your situation you are going to need a screwdriver and possibly spend some money.

Check the connections for both power supply units. If the plugs from the older working one fit onto the motherboard of the newer non-working one just swap them over. If they do not match then take the broken power unit with you and buy another one that has matching connections.

Re-connect the hard drive to the original computer and start it up. All being well you should be able to log in and enter the pass-phrase to unlock your files. If you cannot login to your system at all you have a slightly different problem that the forum should be able to help you with. 

I have heard of a way to by-pass and/or reset the login password however I have never heard of a way of by-passing file-system encryption.

Hope this offers you some hope of gaining access to your files.

                       ===========================================================

Had a sudden thought when you turned on the older computer did you use the same power lead as you used for the newer computer?

Only asking because if different leads were used the loss of power to the newer computer might be down to a broken fuse in the plug.

I quite often have had things stop working and spent many minutes thumping and kicking and a lot of head scratching trying to get it to work. When finally replacing the fuse and the equipment works again I have gone and bashed my head against a wall for over-looking the obvious.

---

### Post by edmund085 on 2011-07-12
@Bachstelze: well, i will try my luck maybe i can still access using a 10.0 ubuntu Live CD version even if it lags and take a long time to boot, maybe 30 mins or so..

@westie457: about the power supply, after few minutes using the old CPU, it has the same problem, it didnt turn on, so i did change the plug and it works in the older CPU, i realise that the plug is defective, I will try to change the plug of the newer CPU maybe it will work, or try to change the fuse maybe it will run, so that I can run ubuntu hard drive on the Newer CPU.

I'll have to cross my fingers, or bet on luck or chance.

---

### Post by edmund085 on 2011-07-13
first thing first... i tried using the Live CD, but heres the problem, i tried looking at the /home/edmund085/Private but theres nothing in there... and also I tried clicking the hard drive where the original Ubuntu OS is and all I get is an error...

Unable to mount location
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by cariboo on 2011-07-13
Can't you just move the power supply from the working system to the one with the broken power supply?

---

### Post by edmund085 on 2011-07-13
@cariboo907: If it is possible I already did that, but the female socket plug of the new motherboard for the power is different from the power supply of the old. They don't really match.

---

### Post by edmund085 on 2011-07-13
or the working system model power supply is ATX 300 Switching power supply, and the broken one is ATX 450, they are totally different because of the plugs.

---

### Post by edmund085 on 2011-07-17
frankly, nothings working the power supply is a total fail, and I dont have any more options but to get those files. All I got is an error that i cannot mount my hard drive, and i cant see my files after following the thread or link that was given.

---

### Post by DZ* on 2011-07-17
> **edmund085 said:**
> frankly, nothings working the power supply is a total fail, and I dont have any more options but to get those files. All I got is an error that i cannot mount my hard drive, and i cant see my files after following the thread or link that was given.

There are two "mounts" in that process. 

First, you need to mount your Ubuntu hard drive where your files are, using a running linux OS (e.g. live CD). Suppose you mounted it to /media/Dsk. Once you've done that, your encrypted files are in /media/Dsk/home/.ecryptfs/edmund085/.Private

Second, you "mount" that to a second location (somewhere outside /media/Dsk) which will contain decrypted files.

In the command that starts with "sudo mount -t ecryptfs", the next argument is where you mounted your files, and then goes "the second location".

---

### Post by edmund085 on 2011-08-10
The power supply is now working. I used to run the hard drive with the Ubuntu OS but is not working. I used the mount thing. And nothing works. Either I don't understand or I am doing it wrong. How about posting the instructions in a Elementary form so that I can understand better or maybe there are some instructions that I did wrong. I just installed Ubuntu and I DON'T have any knowledge to use it. This is my first time to use it and I have problems already.  Frankly, I'm suited Windows since it is taught in school, and the only Operating System I mastered. I want to try something new but sadly on my first time. I had encountered a problem like this, that had risk ALL of MY FILES. Which are currently important, and I need those files before tomorrow comes because it will be deadline. And if I can't submit, I WILL FAIL my MAJOR SUBJECT.

---

### Post by edmund085 on 2011-08-10
can someone please help me. I am begging here. I want get my files, and I will not use anymore Ubuntu. Just get my files out of this drive. Cause I DON'T EVEN understand all those methods all i just do is follow this and follow that and nothings happening. You're giving links that is not working. Just please give me solutions by ANY MEANS POSSIBLE. I don't want to fail my subject. JUST PLEASE PLEASE PLEASE. I AM BEGGING YOU PEOPLE!!!!!!!!! I am running out of time. I dont care if you use a Remote Tool just get my files out. Or post an instruction that even a GRADE 2 kid can understand it. I don't have knowledge or any stored knowledge at all when it comes to UBUNTU. THOSE FILES are very important and I CANNOT afford to LOSE them.

---

### Post by bodhi.zazen on 2011-08-11
> **edmund085 said:**
> can someone please help me. I am begging here. I want get my files, and I will not use anymore Ubuntu. Just get my files out of this drive. Cause I DON'T EVEN understand all those methods all i just do is follow this and follow that and nothings happening. You're giving links that is not working. Just please give me solutions by ANY MEANS POSSIBLE. I don't want to fail my subject. JUST PLEASE PLEASE PLEASE. I AM BEGGING YOU PEOPLE!!!!!!!!! I am running out of time. I dont care if you use a Remote Tool just get my files out. Or post an instruction that even a GRADE 2 kid can understand it. I don't have knowledge or any stored knowledge at all when it comes to UBUNTU. THOSE FILES are very important and I CANNOT afford to LOSE them.

I am willing to help you, but you have not posted the information I need to assist you.

If you encrypted the files, and do not know the password, you are out of luck.

If you encrypted the files, and know the password, and can tell me what you encrypted them with, I can help. Did you encrypt them with Windows or Ubuntu ? Truecrypt ? ecryptfs (encrypted home directory) ? LUKS ?

When you boot a live CD, and mount the partition , what do you see ?

So if you want help here, take a deep breath and provide the information I need to assist you.

If you find those questions too difficult to understand, or the instructions you have been given here too difficult, and you value your data, time to seek professional assistance.

---

### Post by edmund085 on 2011-08-11
k.. I am now calm. lets forget the windows thing. Is there anyway to reinstall the OS or repair the OS so that it will work again? Since the new power supply is fixed. It is backed to its CPU and Motherboard. I tried booting the device but all I get is a black screen and a blinking cursor point. I tried using the LIVE CD. But I don't know if its correct or not, maybe because I don't understand what I'm doing.

---

### Post by bodhi.zazen on 2011-08-11
OK, what hapens when you boot a live CD ? Can you get a desktop ?

---

### Post by edmund085 on 2011-08-11
I see the whole desktop. But i cant access my Hard drive.

---

### Post by bodhi.zazen on 2011-08-11
> **edmund085 said:**
> I see the whole desktop. But i cant access my Hard drive.

"I cant access my Hard drive" - does not really help. What is it you want me to do with that statement ?

What have you done to try to access the hard drive ? What problem did you have ? What error message did you get ? What encryption did you use ?

If you can not provide a better description of your problem you will seriously need professional assistance.

Normally you mount the partitions.

Open a terminal, list your partitions.

```
fdisk -l
```

Then mount them and look for your data. You need to work as root, so 

```
sudo -i
```

You now have a root shell.

```
mount /dev/sda1 /mnt
```

Then browse your partition.

```
gksu nautilus
```

You then need to describe any problem you have or post any error messages you get.

Also, do you know the password you used for encryption ? And what encryption did you use (Truecrypt, LUKS, ecryptfs ???)?

---

### Post by edmund085 on 2011-08-11
I have a really really bad news. I just found out that there is no problem with the power supply. I think its the whole CPU, I just seek out professional assistance, but it turns out that they won't fix my CPU because its Ubuntu. They prefer Microsoft and its the only one they mastered. Sadly in our city, we have 6 Service Centers and not even 1 of them cared to help me because of a different Operating System. So this forum is my last phase of help. I have no other places to go to. I live in Philippines, a third world country, especially i live specifically in a city province area. So please help me and bear with me, cause I have so little time especially I need the files within 10 hours, specifically before 6:00pm afternoon in our time (GMT +8:00). I am now deciding be absent of all my classes from 1:30pm to 6:00pm so that I can get the files I needed in order not to fail.

Problem:
CPU won't start, I have the 40GB Hard Drive with a DVD Reader inside, Pentium IV and 516 memory. The PSU is 450W, ATX with 3 external fans connected excluding the fan from the motherboard and from the PSU itself. CPU fails to boot and keeps on restarting, if it does not restarts, it is on bot no POST or boot, dead silence. I hear a 1 beep then it shut downs, or 2 beeps and it shut downs. The BIOS is AMI.

---

### Post by edmund085 on 2011-08-11
I checked the mother board for BAD Capacitors, but none. And my Motherboard is ECS P4M800 Pro. I don't know how to configure the motherboard. Please help me.

---

### Post by DZ* on 2011-08-11
> **edmund085 said:**
> I just found out that there is no problem with the power supply. I think its the whole CPU
But you can boot from a live CD on that computer, correct? What happens when you run the terminal commands just suggested by bodhi.zazen?

---

### Post by edmund085 on 2011-08-22
tsk... even bad news... I failed my exams and my midterm grade, but since past is past, time to move on. All I need now is the files, my mother didnt agree to buy a new PSU or diagnose the CPU since I failed my midterm exams. So I am running out of hope and luck. I have now placed the Hard drive with its Ubuntu OS in my old CPU, its status is in slave. And the master is another drive which is windows. Now give me a step by step one by one procedure. Think of me as a STUPID USER who don't know anything about computers cause i dont get a **** about your ******* instructions. So lets start with basics to advanced. I am very frustrated and angry so please BEAR with me.

1. Insert live cd on dvd disk drive then let it run. 
2. I have now reach the UBUNTU desktop 
what should I do next? what is the first command I should do or type?

---

### Post by cryptotheslow on 2011-08-22
OK from the LiveCD desktop open a Terminal. It is on the Accessories menu.

Then enter these 2 commands and copy and paste the response back here.

```

fdisk -l

mount

```

---

