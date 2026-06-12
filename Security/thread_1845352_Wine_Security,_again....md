---
title: "Wine Security, again..."
date: 2011-09-16
forum: Security
---

### Post by Dangertux on 2011-09-16
I had a curiousity which was spawned by this thread [http://ubuntuforums.org/showthread.php?t=1845070](http://ubuntuforums.org/showthread.php?t=1845070)

I didn't want to hijack that thread, but I definitely am interested in everyone's thoughts.

There are a lot of generally accepted assumptions about Wine. Like, it  can't get out of your home directory, it won't run windows malware, it  has to have root to do bad things, removing sym links is a good idea, if I encrypt my home directory I'm good. All of  these sound like great ideas, but I became curious as to how well they  actually work. 

Long story short, it seems the only thing that will work is common sense and  Apparmor (and that's not 100%). I took the time to test out a lot of  this, and documented the results for anyone who is interested. It's not a  perfect test but it definitely illustrates that Wine is probably not  the most secure thing out there.

If you'd like to read the results of my testing you may find the link in  my signature  or[here]("http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/"). Please be aware it's rather long, however I would encourage you to read it before simply reiterating "there is no malware that works in linux" or repeating any of the other afforementioned "solutions" as it does address a lot of them.

I am wondering what those of you who use Wine frequently are doing to secure it. If anything.

---

### Post by haqking on 2011-09-16
> **Dangertux said:**
> I had a curiousity which was spawned by this thread [http://ubuntuforums.org/showthread.php?t=1845070](http://ubuntuforums.org/showthread.php?t=1845070)

I didn't want to hijack that thread, but I definitely am interested in everyone's thoughts.

There are a lot of generally accepted assumptions about Wine. Like, it  can't get out of your home directory, it won't run windows malware, it  has to have root to do bad things, removing sym links is a good idea, if I encrypt my home directory I'm good. All of  these sound like great ideas, but I became curious as to how well they  actually work. 

Long story short, it seems the only thing that will work is common sense and  Apparmor (and that's not 100%). I took the time to test out a lot of  this, and documented the results for anyone who is interested. It's not a  perfect test but it definitely illustrates that Wine is probably not  the most secure thing out there.

If you'd like to read the results of my testing you may find the link in  my signature  or[here]("http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/"). Please be aware it's rather long, however I would encourage you to read it before simply reiterating "there is no malware that works in linux" or repeating any of the other afforementioned "solutions" as it does address a lot of them.

I am wondering what those of you who use Wine frequently are doing to secure it. If anything.


NIce, good interesting read in the report.

Not a Wine user myself, but interesting to see how the often blanket statements are often flawed.

as i always say, best tool in any security layer is the User...or of course the worse tool ;-)
cheers

---

### Post by Dangertux on 2011-09-16
Glad you liked it. I think it's second nature for a lot of people (I've caught myself doing it too). To say oh hey Windows Malware doesn't work.

And yes, this is a highly unlikely scenario, but it's nice to know what possibilities are out there. 

I suppose the circa 2001 adage of "be careful what you download" still holds true to some extent.

---

### Post by haqking on 2011-09-16
> **Dangertux said:**
> Glad you liked it. I think it's second nature for a lot of people (I've caught myself doing it too). To say oh hey Windows Malware doesn't work.

And yes, this is a highly unlikely scenario, but it's nice to know what possibilities are out there. 

I suppose the circa 2001 adage of "be careful what you download" still holds true to some extent.


Yeah i try to not use the term malware as it is a broad statement for linux, i usually seperate Viruses out of it, and then leave the rest as ambiguous.

Can malware run on Linux...yes, likely ? depends on how you administer your linux box

Can Linux get a virus (malware specific) unikely as there no current known ones in the wild but times change !

user user user beware, layered approach and keep on top of things.

---

### Post by jramshu on 2011-09-16
Interesting indeed DT. 

Thanks for sharing.

---

### Post by tgm4883 on 2011-09-19
I should have just skipped to the conclusion. 

Wine (like any other code) is a potential security risk. You system could be completely owned by running a simple bash script. 

Please realize that Security and Ease of use are on the opposite ends of a scale, and Ubuntu falls somewhere in the middle (maybe even leans toward ease of use). 

There are tools available (AppArmor) in order for you to help protect your system (There are even graphical tools available for AppArmor, although they do need to be packaged for Ubuntu)

Don't look at it from the attackers perspective, instead look at it from the defenders. You mention that because of the lack of use of AppArmor that an attacker wouldn't have to worry about it. Flipping that around, because of the use of AppArmor the defender doesn't have to worry about the damage an attacker could do.

As previously stated, I'm not entirely sure what the point of your post was other than to say that an OOTB Wine installation is vulnerable to Trojans. I really would have liked to see you configure AppArmor and show what you were able to access after that. You complain that there aren't any good AppArmor profiles for Wine yet you do nothing about it.

---

### Post by Dangertux on 2011-09-19
You have some valid points, however it was just an analysis of what is considered the commonly accepted best practices for Wine.

I didn't create an apparmor profile for 2 reasons, one if apparmor containment works properly it would in fact limit the access greatly, without additional exploitation provided. Two the vast majority of users do NOT know how to configure apparmor properly (usually the first time they put a profile into enforce mode and it breaks the app they quit).

I think you missed the point in that the exercise was to run Windows code through Wine and see what exactly is available to it. I am more than aware of many countermeasures that would have stopped this really basic test  from working. It was just to illustrate that a backdoored Windows executable CAN yield some access to content EXTERNAL to the Wine "confinement" area.

Also to answer your question about thinking from an attackers perspective, I think that logic is sort of flawed, but also has a valid reasoning as well. If you think only from a defender's point of view you may be missing the big picture. Just my opinion though.

It was more of a test of "boundaries" if you will, to illustrate how far Windows code can go. Yes as I said in the conclusion it's simply a trojan, however anything that an individual can do with a remote administration tool can be automated once access is granted. 

I agree with you that I should have given an example Wine profile for apparmor. I was a little short of time as it was a Friday afternoon, and after I came back around to it I didn't think it was really relevant in the scope of the discussion since I flat out said Apparmor can and will limit the access Wine has just fine.

The entire example was spurred by a question in another thread posed as "can Windows malware effect Linux through Wine" the example was to show, yes it can, to varying degrees of severity.

In an overall security model this threat would be miniscule. That being said, I highly doubt most home users trying to play a Windows game have created a complicated, and thorough security model, and even less likely have created a plan of action for when the model fails.

Security will always fail. No matter what, it is not about being secure, it is about determining how much risk you can accept for a given application or system. It always has been. So if having a Windows Trojan compromise your data is a serious risk that you can't accept, you have to implement apparmor or find an alternative method to running your Windows app. If it is an acceptable risk you note that it's there and move on implementing the best practices you can along the way.

EDIT : After actually getting some time to research your thoughts about Apparmor. I've learned a few things. One Apparmor is a multi-functional approach when concerning Wine, Wineserver and the software being run. First off, to even work Wine and Wineserver need VERY permissive settings. Which in and of itself is bad. You can accomplish most of what needs to be done for the specific applications wine will be running through hat changes, however it leaves you with a few problems. One, there is absolutely NO way to stop Wineserver from making Linux system calls, which is bad. Two, the permissions you have to allow the profiles is so ubiquitous it almost negates the point of using Apparmor. I'm not an apparmor pro by any stretch of the imagination, but it would seem you have to make a very specific profile for every application you're running. Considering the nature of files that are commonly backdoored, I believe my original argument holds water.

---

