---
title: "24 Things I've Learned As A Developer Living On Ubuntu For A Weekish"
date: 2017-12-30
forum: The Cafe
---

### Post by jonnyasmar on 2017-12-30
Hello all!

I just put together a little piece about my experience transition to Ubuntu full-time and thought you all might enjoy the read:

[https://medium.com/@jonnyasmar/24-things-learned-as-software-developer-on-ubuntu-for-a-weekish-5b7b0da5d4b5](https://medium.com/@jonnyasmar/24-things-learned-as-software-developer-on-ubuntu-for-a-weekish-5b7b0da5d4b5)


Thanks!

---

### Post by sisco311 on 2017-12-30
Not a support request. Moved to the *Cafe*.

---

### Post by litlesam on 2017-12-30
What a interesting and while written read!

Many Thanks

---

### Post by again? on 2017-12-30
> **jonnyasmar said:**
> Hello all!

I just put together a little piece about my experience transition to Ubuntu full-time and thought you all might enjoy the read:

[https://medium.com/@jonnyasmar/24-things-learned-as-software-developer-on-ubuntu-for-a-weekish-5b7b0da5d4b5](https://medium.com/@jonnyasmar/24-things-learned-as-software-developer-on-ubuntu-for-a-weekish-5b7b0da5d4b5)


Thanks!
Good article about the benefits and personal pleasure of using Linux without bashing other operating systems.
Linux doesn't suit everyone, but you being a developer and self confessed tinkerer, thought you would have been here long ago.

---

### Post by uRock on 2017-12-30
A good read. I'm glad you're having a good time with Ubuntu.

---

### Post by jonnyasmar on 2017-12-30
Thanks guys!

@guber2 -- I'm surprised as well, myself! lol. I was just always content with Windows/Mac, I guess.

Definitely loving it, though! :)

---

### Post by wrongusername2 on 2017-12-30
Hi,
          I am also Windows developer trying to make Ubuntu my primary machine. Following is my experience in  past one month as a *user*. 

1) OS is transparent and that makes it easy to work. Editing config file is cumbersome but you are confident that the changes WILL take effect. This is not the case with Windows at tall, There are zillions of solution for every problem, one may spend whole day trying each one of them and in the end none of them work. 

2) OS documentation seems to be written by Engineer unlike MSDN. I was able to learn about file system, boot sequence by investing just couple of hours. At least I know the rough steps. This is not the case with MSDN. I have spent majority of my life reading them. 
     [URL="https://wiki.ubuntu.com/UEFI/SecureBoot/Testing?action=show&redirect=SecurityTeam%2FSecureBoot#Testing_Secure_Boot"]https://wiki.ubuntu.com/UEFI/SecureBoot/Testing?action=show&redirect=SecurityTeam%2FSecureBoot#Testing_Secure_Boot
[/URL]     [URL="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/installation_guide/ch-boot-init-shutdown#s1-boot-process-basics"]https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/installation_guide/ch-boot-init-shutdown#s1-boot-process-basics
[/URL]
3) tmp folder
   I did not know the data stored in tmp folder will not be stored

4) DD command
   I created a image using DD command and restored it successfully. Simplicity of the command amazed me. (As a developer my specialization is Storage product for Microsoft Exchange server).

5) SimpleScreenRecorder
  This is an amazing tool to record desktop activity. I installed Ubuntu on few laptops and this is the first tool I install on a brand new OS. Helps record the things that I am doing.

6) Remembering Linux commands (~, mount, fdisk, find etc..)
   I make tiny audio clips and listen to them couple of time and that makes drinking from hose somewhat smooth.

7) Audio stack is hard to understand. (QaMixer)  

8) Color Management (dispcal). I am using Argyll for color management and it is not that easy work with..

9) Package management seems to be designed assuming that the machine is connected to internet. I came to know about apt-offline and yet to use it.
 
Thanks

---

### Post by jonnyasmar on 2017-12-31
Thanks for sharing your findings wrongusername2!

4) This particularly amazes me as well! Backup/restore has always been such a convoluted, bloated process in Windows & Mac. I have yet to restore an image, but I've been researching this to set up some automation and it's an amazing tool.

5) That's neat! Do you record tasks and such to go back and reference? I've never thought to do this except for tutorials/docs/etc.

---

### Post by virgosun on 2018-01-01
Hello, 2 years seasonal experience with Linux. Yet this is correct 
> 'There are zillions of solution for every problem, one may spend whole   day trying each one of them and in the end none of them work.'
1 of the problem, I don't find a solution:
I have a Live ISO partition with a Persistence partition which is growth to 8GB as in the picture below
How do I convert from Live Persistence to a full installation but still keep all my application, setting, etc, eg, keep the whole Persistence partition?

Update
Never mind, I did it by rsync

---

### Post by jonnyasmar on 2018-01-01
Glad you figured it out, virgosun!

---

### Post by wrongusername2 on 2018-01-01
> **jonnyasmar said:**
> Thanks for sharing your findings wrongusername2!
5) That's neat! Do you record tasks and such to go back and reference? I've never thought to do this except for tutorials/docs/etc.

Most likely I will forget these steps in another 6 months so it is better to record. I keep record in document also because I can copy and paste :-) So each medium has  its own advantage.

---

### Post by jonnyasmar on 2018-01-01
Good thinking, wrongusername2! Definitely going to check out SimpleScreenRecorder :)

---

### Post by pauljw on 2018-01-02
Good read!  Thanks for sharing your thoughts.

---

### Post by mastablasta on 2018-01-03
> **wrongusername2 said:**
> 
2) OS documentation seems to be written by Engineer unlike MSDN. 

actually it is mostly written by users. many of them are not engineers, but they have to follow the preset standards.

> 
9) Package management seems to be designed assuming that the machine is connected to internet. I came to know about apt-offline and yet to use it.


this is one of the things that was bothering me as well. It is all aimed at online PC. binary packages are rare, and although there are .deb and source files, they are not as secure or convenient.

however, recently snaps (and various other packs) appeared that solve this issue. they are secure ("sand boxed") and you can install them while offline. the downside is that their size is larger (just like programs in windows), but on the other hand disk space is not that expensive anymore.

---

### Post by virgosun on 2018-01-03
What I found, supposed I am more used to Windows, and as a desktop user: Ubuntu is open-source, but Windows supports all hardware. So for full hardware usage, I use Windows, for very specific reason, I use Ubuntu.

---

### Post by pauljw on 2018-01-03
> **virgosun said:**
> What I found, supposed I am more used to Windows, and as a desktop user: Ubuntu is open-source, but Windows supports all hardware. So for full hardware usage, I use Windows, for very specific reason, I use Ubuntu.

This misconception really bugs me, and I'm not directing this at you virgosun, but I guess at the world in general.  MS/Windows doesn't support jack, rather it is supported by hardware manufacturers and software programmers and Linux is not.  Linux devs have to reverse engineer drivers for any and all hardware that doesn't supply said drivers and that takes a lot of time.  This is why we don't get to play with the latest and greatest hardware and that we need to buy our hardware based on whether or not is has linux compatibility.  

We shouldn't blame our OS of choice for things that are outside the scope of its responsibility.  Microsoft would be useless if hardware manufacturers didn't support it.  END RANT

Paul

---

### Post by uRock on 2018-01-03
> **virgosun said:**
> What I found, supposed I am more used to Windows, and as a desktop user: Ubuntu is open-source, but Windows supports all hardware. So for full hardware usage, I use Windows, for very specific reason, I use Ubuntu.

Was that meant to be a joke? I have a pile of hardware that is no longer supported by Windows, yet is plug-n-play in Linux.

---

### Post by virgosun on 2018-01-03
I understand that you mean the overall Windows's drivers base is not the sole effort of MS. Besides, I think MS have some kind of strive in integration, how ever.

---

### Post by virgosun on 2018-01-03
> **uRock said:**
> Was that meant to be a joke? I have a pile of hardware that is no longer supported by Windows, yet is plug-n-play in Linux.

:D that's real, for the joke, what lead many people to Linux, me included

---

### Post by Geoffrey_Arndt on 2018-01-03
The real "Joke" is how anti-trust & monopoly laws are not consistently enforced since the 60's.   So, the end result (for the "consumer" market) is if you want your PC to sell, then you pre-design it for Windows or MacOS and test it for the same OS's.   About 15-25% of PC hardware is intended for more than just the consumer market (mainly all Intel machines).   These are intended for the Govt, Edu, Science and Business markets.    Those are the machines largely compatible with Linux and BSD (Unix).

If one knows that upfront, you can adjust your buying habits accordlingly.

In the world of broader computing devices (phones, servers, IoT and all 3 classes of Mainframes (mini-mid-super), . . . . Linux absolutely rules.     This is due to capability versus marketing and OEM incentives.

---

### Post by virgosun on 2018-01-03
> **Geoffrey_Arndt said:**
> The real "Joke" is how anti-trust & monopoly laws are not consistently enforced since the 60's.   So, the end result (for the "consumer" market) is if you want your PC to sell, then you pre-design it for Windows or MacOS and test it for the same OS's.   About 15-25% of PC hardware is intended for more than just the consumer market (mainly all Intel machines).   These are intended for the Govt, Edu, Science and Business markets.    Those are the machines largely compatible with Linux and BSD (Unix).

If one knows that upfront, you can adjust your buying habits accordlingly.

In the world of broader computing devices (phones, servers, IoT and all 3 classes of Mainframes (mini-mid-super), . . . . Linux absolutely rules.     This is due to capability versus marketing and OEM incentives.

Ah yeah, there are sectors that invest their back end infrastructure in Posix. But for front end I don't think they can avoid Windows or macOS.

---

### Post by virgosun on 2018-01-03
How about this analysis [Usage_share_of_operating_systems]("https://en.wikipedia.org/wiki/Usage_share_of_operating_systems")? 
Many parties may ague about their claimed share of the market. I think those figure need more statistic, breakdown to geo-economic sub-division. 
Where as, server OS characteristics in developed counties are not same as the under-developed countries, regardless of the operating sectors, except FDI sector.

---

