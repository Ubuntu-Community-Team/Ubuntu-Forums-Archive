---
title: "Ubuntu Tweak 06. Tried to install on 12.04. No go."
date: 2011-12-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2011-12-23
I am testing Ubuntu 12.04 and wanted to see if I could Install Ubuntu Tweak 06. I followed the commands 
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
and when I came to the last one it gave me the message. Unable to locate package ubuntu-tweak. Doesn't look like it will run in 12.04 yet.

---

### Post by crazy bird on 2011-12-23
If you look at the overview of the available packages you should noticed already that 12.04 is not supported yet. Even if you have to select your correct version you had to notice that there are only packages available for Ubuntu 7.10 u/i 11.10. 
 
So, just wait till april 2012. Maybe then you get a correct PPA. And beside that, i'm nopt suprtpised to see that some apckages doesn't support 12.04 yet since 12.04 is still in development and not released for the public.
 
Even on [the official site]("http://ubuntu-tweak.com/") you don't get any packages for 12.04. The latest version supported is 11.10.

---

### Post by JRV on 2011-12-23
After reading your post I tried:

```
add-apt-repository ppa:tualatrix/next
apt-get update
apt-get install ubuntu-tweak

```

That didn't work either.

---

### Post by cariboo on 2011-12-23
Just change the version to Oneiric, in Software Sources. I've had it installed and updated, for quite a while.

---

### Post by crazy bird on 2011-12-23
> **cariboo907 said:**
> Just change the version to Oneiric, in Software Sources. I've had it installed and updated, for quite a while.
 
That's not the most beautiful solution since you want to avoid mixing older package versions with newer package versions. Best is to wait till Ubuntu Tweak is available for 12.04 with an official package.

---

### Post by sammiev on 2011-12-23
> **crazy bird said:**
> That's not the most beautiful solution since you want to avoid mixing older package versions with newer package versions. Best is to wait till Ubuntu Tweak is available for 12.04 with an official package.

You are correct but I found the same thing with Jupiter a few days back. So for now it's a must have. :)

---

### Post by dino99 on 2011-12-23
> **irv said:**
> I am testing Ubuntu 12.04 and wanted to see if I could Install Ubuntu Tweak 06. I followed the commands 
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
and when I came to the last one it gave me the message. Unable to locate package ubuntu-tweak. Doesn't look like it will run in 12.04 yet.

And that was your christmas requested gift ? If not, dont complaint :)

---

### Post by irv on 2011-12-23
I have it installed now. How I did it was to go to: Ubuntu Tweak and download the .deb file. [https://launchpad.net/ubuntu-tweak/+download]("https://launchpad.net/ubuntu-tweak/+download")
ubuntu-tweak_0.6.0-1~oneiric1_all.deb (md5) and I used Gdebi to install it.
[ATTACH]209624[/ATTACH]

---

### Post by PaulW2U on 2011-12-23
There is a Precise version of Ubuntu Tweak available from a "testing" PPA. I'm not at a PC at the moment but Google will give you the PPA location on Launchpad.

It works fine although sometimes very slow to start up. There have been several updates in the last week.

---

### Post by irv on 2011-12-23
> **PaulW2U said:**
> There is a Precise version of Ubuntu Tweak available from a "testing" PPA. I'm not at a PC at the moment but Google will give you the PPA location on Launchpad.

It works fine although sometimes very slow to start up. There have been several updates in the last week.

Here is the website: [http://ubuntulady.wordpress.com/2011/12/22/ubuntu-tweak-0-6-is-now-available-for-precise-and-other-ubuntu-versions/]("http://ubuntulady.wordpress.com/2011/12/22/ubuntu-tweak-0-6-is-now-available-for-precise-and-other-ubuntu-versions/")
I just followed the instructions:
Commands:
```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
And I now have the test version for Precise installed.

---

### Post by dmoconnell on 2011-12-23
heres the PPA Paul mentioned (remember its Unstable version

```
ppa:ubuntu-tweak-testing/ppa
```

and a link to the Ubuntu Tweak Testing Launchpad page

[https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa]("https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa")

Dm

---

### Post by JRV on 2011-12-25
> **JRV said:**
> After reading your post I tried:

```
add-apt-repository ppa:tualatrix/next
apt-get update
apt-get install ubuntu-tweak

```

That didn't work either.

It Works now.

---

### Post by irv on 2011-12-25
> **JRV said:**
> It Works now.

As I said in post #8 and #10, I have it installed and working. I did want to test the test version release along with 12.04.

---

### Post by 1roxtar on 2012-01-09
I simply downloaded the .deb from the Ubuntu Tweak website and everything worked out of the box.  I've had no crashes or problems running it.  So far it's been working as good as it does on my 11.10 machines.

---

### Post by sammiev on 2012-01-09
> **1roxtar said:**
> I simply downloaded the .deb from the Ubuntu Tweak website and everything worked out of the box.  I've had no crashes or problems running it.  So far it's been working as good as it does on my 11.10 machines.

I have been using the 07 version and noticed they fixed a few bugs. So far no issues with 07.

---

### Post by kansasnoob on 2012-01-09
> **crazy bird said:**
> That's not the most beautiful solution since you want to avoid mixing older package versions with newer package versions. Best is to wait till Ubuntu Tweak is available for 12.04 with an official package.

There is nothing at all wrong with manually changing the source version of a PPA for testing purposes. Remember that all PPA's are regarded as "untrusted" sources anyway :D

---

