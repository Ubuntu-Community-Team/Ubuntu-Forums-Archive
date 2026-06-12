---
title: "Dapper vs. Suse 10.1"
date: 2006-05-20
forum: The Cafe
---

### Post by emperon on 2006-05-20
Hello I just want share my own opinions about Dapper and Suse 10.1.

I am using ubuntu/kubuntu for about 10 months as my primary desktop machine. Recently, I just wanted to give a shot to Suse of which a brand new version released. Also I was using Suse before I met ubuntu.

At first sight, Suse 10.1 seemed to be extreemly polished and professional. Excellent installation and hardware recognition is worth mentioning. 

After the installation phase my next step to set up  full multimedia support. At that point I understood why ubuntu is superior comparet to Suse. Don't take it wrong. There are very detailed posts about multimedia support in Suse community forums but...

As most, I was a bit anticipated with RPM mechanism it self. It is a bit fragile compared to debian's. So  my problem was about Yast. Many people in Suse community are unhappy about Yast. Instead they offer alternative solutions like apt or smart. I personally found Yast very slow and buggy. Synaptic is like a breeze compared to it.
So you see, default built in package manager is crap in Suse. 
Also repositories are a bit problem. Some packages at some mirrors are broken. And you have to deal with directory names for adding new repositories. Even manually dealing with source file in ubuntu is much better

Thirdly ,Novel is less responsive than ubuntu in adding most recent packages. 

They have KDE 3.5.1 default installed and Gnome 2.12. But most surprisingly Mono 1.13. I can understand this ,most probably they freeze out the development at some time. But I know from my earlier experience, Novell is always slow on this.

Finally the community. This is what makes ubuntu number 1 distro. As a comparison if you look at main stream Suse forum's you will see Ubuntu forums has about 5 x more registered user and about 10 x more posts. The forum structure itself on suse is complicated and most posts are still on Suse 9.3 or 10.0. Ubuntu is a clear winner on this manner. You can find any info in Ubuntu forums.

I also am dissapointed on Mono for Suse. Mono is personally important for me. I am working as a Software developer and my company has chosen .NET as development platform. Earlier I was dealing with Java. You probably know the flamewars on .NET and Java or J2EE. Personally I don't like Sun's keeping java closed source so in this Sense Java is as evil as .NET to me. But I also hate being puppet of Microsoft on this sense. So philosophically Mono wins my heart. It is open souce, and powerful as .NET (though quite immature and has a much weaker community now). But I really want mono to be the main stream linux development platform. And back to Suse, well..., I am still unable to install the monodeveloper there, and it does not come with Suse. I found Suse's mono support as inadequate althogh mono and suse both come from Novell. That's a big minus to me

However, Suse is much faster than ubuntu and is at least as stable as ubuntu. Nevertheless with all those points above: Ubuntu Is The Way !

---

### Post by ComplexNumber on 2006-05-20
>  As most, I was a bit anticipated with RPM mechanism it self. 
why do you say that immediately after you say this:
> Also I was using Suse before I met ubuntu.

the question is, have you had any experience with rpm at all?


> 
Personally I don't like Sun's keeping java closed source so in this Sense Java is as evil as .NET to me.
not any more. although the virtual machine still is still closed (i think)

---

### Post by helpme on 2006-05-20
Just some comments, as I am also playing around with Suse 10.1 at the moment.

[QUOTE=emperon]
After the installation phase my next step to set up  full multimedia support. At that point I understood why ubuntu is superior comparet to Suse. Don't take it wrong. There are very detailed posts about multimedia support in Suse community forums but...
[/quote]
Setting up multimedia support really isn't that hard (if the package manager would work that is, see below). All you really need to do is add the packmann repository:
[http://en.opensuse.org/Additional_YaST_Package_Repositories#Packman](http://en.opensuse.org/Additional_YaST_Package_Repositories#Packman)

[QUOTE=emperon]
As most, I was a bit anticipated with RPM mechanism it self. It is a bit fragile compared to debian's. So  my problem was about Yast. Many people in Suse community are unhappy about Yast. Instead they offer alternative solutions like apt or smart. I personally found Yast very slow and buggy. Synaptic is like a breeze compared to it.
So you see, default built in package manager is crap in Suse. 
Also repositories are a bit problem. Some packages at some mirrors are broken. And you have to deal with directory names for adding new repositories. Even manually dealing with source file in ubuntu is much better
[/quote]
This isn't a rpm problem. The alternatives you mention, that is apt and smart, work very well and they both use rpm too.
However, the package management with yast has in my experience been functional but not really shining. So what the Suse folks did now is, they developed a whole new backend for package management combining the things they had with yast and if I understand it correctly the red carpet stuff.

And while this does sound great on paper and probably will be great in the future, at the moment it's not very well integrated into the system yet and it's simply incredibly broken, as in, it doesn't work. 

So in my experience, if you want to enjoy the newest Suse, go for the alternatives. I tried smart now for the first time and it's really good.

[QUOTE=emperon]
Thirdly ,Novel is less responsive than ubuntu in adding most recent packages. 

They have KDE 3.5.1 default installed and Gnome 2.12. But most surprisingly Mono 1.13. I can understand this ,most probably they freeze out the development at some time. But I know from my earlier experience, Novell is always slow on this.
[/quote]
I think the problem here is that 10.1 got delayed for months as they tried to integrate the new package manager. They probably concentrated on this, but stuck with the versions that were planned otherwise.
However, you'll at least be able to get newer versions of Gnome and KDE (in fact, KDE3.5.2 is already available). 
[Click]("ftp://ftp.mirrorservice.org/sites/ftp.suse.com/pub/suse/i386/supplementary/KDE/update_for_10.1")
No clue about mono though, sorry.

[QUOTE=emperon]
Finally the community. This is what makes ubuntu number 1 distro. As a comparison if you look at main stream Suse forum's you will see Ubuntu forums has about 5 x more registered user and about 10 x more posts. The forum structure itself on suse is complicated and most posts are still on Suse 9.3 or 10.0. Ubuntu is a clear winner on this manner. You can find any info in Ubuntu forums.
[/quote]
I agree, I never understood why Suse didn't try to provide one official forum.

---

### Post by Rackerz on 2006-05-20
I've tried Suse 10.1 and I didn't like it that much, partly because the support isn't that great. The reason I chose Ubuntu is because there's still people round here to put up with us N00beh's!

---

### Post by jambazi on 2006-11-02
_Here is my Linux Story_

I use to be a staunch Suse user since version 7.3 then dropped it for RH9 then Switched to FC1-3 then Mandrake/mandriva and Ubuntu. I can say I have quite some experience with most major  distros. 

Anyhowz I decided to switch to Suse 10.1 recently. I consider myself a linux power user since use linux for my daily computing needs, so I need to have support for almost everything from an office suite, multimedia etc the whole works.

Suse installation was a breeze, graphics are pretty cool, Yast is a good idea but still needs some work. It is just way to slow. 

I have never experienced a package manager that takes that long to get a list of updates or even just to update sources.

Yum repos and apt work like a charm, but I was hoping to have an automated update thru yast like Windows Update. Mp3s wont play, none of the multimedia apps will play nothing not even DVDs, browsers lack crucial plugins like flash. Anyway boot up seems sluggish.

System Specs: P4 with 512mb ram and 250gig drive

Ubuntu and Mandriva have served me well since time in memorial but I wish I could say the same for the new Suse install. I think before the end of this post I will have decided to switch back to dapper.

Personally no offence to anyone, but I think Suse 10.1 sucks if lacks support for mp3s and other music formats. I think I will stick to my Ubuntu and Mandriva till kingdom come or until Suse matches its looks to functionality.

---

### Post by MaximB on 2006-11-02
but mp3,DVD's and other media is "codecs" problem not distro's problem
you can install the codecs on any distro and play any media (I am not talking here about the legal issue).

---

