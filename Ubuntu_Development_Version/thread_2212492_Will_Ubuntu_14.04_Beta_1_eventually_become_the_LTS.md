---
title: "Will Ubuntu 14.04 Beta 1 eventually become the LTS or normal release?."
date: 2014-03-21
forum: Ubuntu Development Version
---

### Post by coolbreeze472 on 2014-03-21
Hi

About a week ago I downloaded and installed Ubuntu 14.04 Beta 1 intending to update my way to the final release (because I was excited and because I wanted to get a head start). My question is this: if I continue to update it, what am I going to end up with a few months from now...the LTS?. The normal release?. When I first installed it I saw the word "LTS" in a few places during the installation (and based on a few things I've read) I was under the impression that the beta 1 (which I have installed now) will eventually become the LTS - however, when I run "lsb_release -a" it just says "Ubuntu 14.04" "Trusty Tahr" "Development Channel" but I don't see "LTS". So do I have the LTS or normal release installed?.

Also, once it becomes the final release, will I need to change repos?.

Thanks for your input, CB

---

### Post by Elfy on 2014-03-21
*Thread moved to **Ubuntu +1**.*

You will have the same as anyone installing it once it is released - with the exception that you will also have all the updated packages unless you remove them.

---

### Post by coolbreeze472 on 2014-03-21
Thank you for your reply. Will I have the LTS or regular release though once I'm finished updating my way up to the final version?.

---

### Post by grahammechanical on 2014-03-21
Actually, it is

> Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty

It is the development  branch because it is 14.04 under development and is not yet 14.04 LTS. And lsb-release is just a text file. It will be updated when we update after release day and then we will no longer see "development branch."

Have you looked at System Settings>Details? Or the login screen? What do those say? Ubuntu 14.04 LTS on my machine. For much of the last five months it was "13.10" because the next release of Ubuntu is built upon the last release and the labels and logos are not changed until the development cycle is well past the mid point.

So, to answer your question. You do not have either the LTS or the "normal" (standard/interim) release installed. You have a development release installed.

Regards.

---

### Post by coolbreeze472 on 2014-03-21
Thank you for your reply. I understand that I don't have the LTS at the moment but what will I have once I have updated my way to the final release?. For example, if I continue updating for the next few months, what will I eventually end up with...the LTS or normal release?. What will the Ubuntu 14.04 Beta 1 I currently have installed eventually become?.

---

### Post by howefield on 2014-03-21
You will have the LTS 14.04.

---

### Post by coolbreeze472 on 2014-03-21
Thank you very much, I was hoping that would be the answer :). I'm one of those people who don't like upgrading every six months so I wanted to have something installed that would stick around for awhile.

---

### Post by marco-parillo on 2014-03-21
> You will have the LTS 14.04.

If you apply updates, your packages will get upgraded, but, if a package were to be entirely removed from the final 14.04 distribution, your copy will not get removed by applying normal updates, right? Only an dist-upgrade?

---

### Post by su:bhatta on 2014-03-21
I do not know which flavor of Ubuntu Beta you installed (e.g Xubuntu,Lubuntu, Gnome) but I would like to add:
Ubuntu LTS release will be supported for 5 years, but Ubuntu Gnome, Xubuntu LTS release are supported for 3 years and not 5.

Since Ubuntu does not participate in Alpha, Beta releases, I am guessing, you have one of the flavors installed. 
So it just might be that your installation is supported for 3 years.

---

### Post by coolbreeze472 on 2014-03-21
I installed Ubuntu v14.04 Beta 1 and I think I downloaded it from here....

[http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/beta-1/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/beta-1/)

Interesting, I have been wondering all this time why there was no Unity installed but since I prefer the Gnome Shell, it is just as well. So...I guess I have the Gnome version that will later become Ubuntu 14.04 GNOME LTS which is supported for 3 years :)

---

### Post by su:bhatta on 2014-03-21
> **coolbreeze472 said:**
> I installed Ubuntu v14.04 Beta 1 and I think I downloaded it from here....

[http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/beta-1/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/beta-1/)

Interesting, I have been wondering all this time why there was no Unity installed but since I prefer the Gnome Shell, it is just as well. So...I guess I have the Gnome version that will later become Ubuntu 14.04 GNOME LTS which is supported for 3 years :)

Yes, you have Ubuntu Gnome Beta installed and it will be supported for 3 years. [http://www.omgubuntu.co.uk/2014/03/ubuntu-gnome-ups-lts-support-period-three-years](http://www.omgubuntu.co.uk/2014/03/ubuntu-gnome-ups-lts-support-period-three-years)
Ubuntu will come out with a Beta2 release sometime 27th March if I remember correctly, and that will be supported for 5 years.

If you like gnome, stick to it. 
Ubuntu by default came with Gnome shell 3 years back, then Unity was developed. :)

---

### Post by coolbreeze472 on 2014-03-21
I also installed Kubuntu 14.04 from this link...

[http://cdimage.ubuntu.com/kubuntu/releases/trusty/beta-1/](http://cdimage.ubuntu.com/kubuntu/releases/trusty/beta-1/)

I think I read that it was also an LTS. Can anyone confirm this please?. Thanks again!.

---

### Post by deadflowr on 2014-03-21
> **coolbreeze472 said:**
> I also installed Kubuntu 14.04 from this link...

[http://cdimage.ubuntu.com/kubuntu/releases/trusty/beta-1/](http://cdimage.ubuntu.com/kubuntu/releases/trusty/beta-1/)

I think I read that it was also an LTS. Can anyone confirm this please?. Thanks again!.

Yes.

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
> **coolbreeze472 said:**
> What will the Ubuntu 14.04 Beta 1 I currently have installed eventually become?.Antique software of only historical interest.

Sorry, I have CSS, compulsive smartass syndrome. I wonder why I found this in the "unanswered" list. Maybe because it was moved?

---

### Post by deadflowr on 2014-03-21
> **Dreamer Fithp Apprentice said:**
> 
Sorry, I have CSS, compulsive smartass syndrome. 

Is it contagious?

---

### Post by su:bhatta on 2014-03-21
> **Dreamer Fithp Apprentice said:**
> Antique software of only historical interest.

Sorry, I have CSS, compulsive smartass syndrome. 

:) It is my fault I guess, I forgot to mention Kubuntu in Post#9.
That confused the OP I think.

---

### Post by Elfy on 2014-03-22
[https://lists.ubuntu.com/archives/ubuntu-release/2014-February/002783.html](https://lists.ubuntu.com/archives/ubuntu-release/2014-February/002783.html)

[https://lists.ubuntu.com/archives/ubuntu-release/2014-March/002803.html](https://lists.ubuntu.com/archives/ubuntu-release/2014-March/002803.html)

From the horse's mouth ...

---

### Post by Chanath on 2014-03-22
> **coolbreeze472 said:**
> I installed Ubuntu v14.04 Beta 1 and I think I downloaded it from here....

[http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/beta-1/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/beta-1/)

Interesting, I have been wondering all this time why there was no Unity installed but since I prefer the Gnome Shell, it is just as well. So...I guess I have the Gnome version that will later become Ubuntu 14.04 GNOME LTS which is supported for 3 years :)

Just keep on updating and dist-upgrading and you'd have your 14.04 LTS. What you have right now is the Ubuntu Gnome Edition, and if you need Unity, just install it. Then you'd have both, the Ubuntu and the Ubuntu-Gnome 14.04 LTS. :P

Good luck!

---

