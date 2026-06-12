---
title: "My experiences installing -&gt; Back to Win7"
date: 2012-10-10
forum: Testimonials &amp; Experiences
---

### Post by gmseed on 2012-10-10
Hi

Every so often I get a new laptop and try setting it up as a developer m/c and after a few days are forced to give up. Clearly, for guru linux/ubuntu guys my issues are no big deal but for linux newbies they are big deals and very off putting.

For what it's worth here is my latest experience:

1) Installed the latest Ubuntu 12.04/32bit on my Sony VAIO i5 laptop. Installation went ok.

2) The battery charge indicator in the main menu always reads "(0:03)" when charging. Although I can view the options dialog and see stats on charge/discharge it always reads "(0:03)". This is poor as the battery indicator is a key component.

3) There is no built-in screensaver and after the elapsed power down period it makes the screen a weird black/white image. After moving the mouse the screen flickers badly. I followed the low-level setup of a screensaver suggested at [http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/) but each time I reboot the laptop it's back to no screensaver.

4) Although I set the screen brightness to my required level every time I reboot the laptop it's reset back to max. brightness. I posted on the Ubuntu forum about resolving this issue and again faced with low-level setup instructions that after reboot don't work.

5) It appears that by default OpenJDK is installed rather than JDK. Although Oracle's JDK runs on billions of devices Ubuntu is opting for the OpenJDL variant. To use JDK1.7_u7 I was then faced with first removing the OpenJDK. I couldn't find a software manager JDK and downloaded the latest and installed, which again could have been a lot easier.

6) Next I wanted to install Eclipse Juno. I see that the software manager supports 3.7, so although I wanted 4.2 I thought ok I'll go for the shipped version. After installing Eclipse 3.7 via Ubuntu package manager it failed to load and refers to a log file, which indicates that can't find libs in .swt/... folder. Others have experienced the same issue; eg the stackoverflow page: [http://stackoverflow.com/questions/10165693/ubuntu-eclipse-cannot-load-swt-libraries-not-opening](http://stackoverflow.com/questions/10165693/ubuntu-eclipse-cannot-load-swt-libraries-not-opening) which gives the solution of forming a link that points .swt/... to the /usr folder:

ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86/

OK. I managed to get Eclipse loading. 

7) I then installed the Android ADT plugin into Eclipse and everything appeared to go well until the restart after which the user is "supposed" to be presented with the option to specify the Android SDK. I never did get this option and have still been unable to find how to specify the SDK. After a couple of forum posts I gave up.

8) So, I next downloaded Eclipse Juno 4.2 direct from Eclipse's website and installed in a local folder. This runs fine. So, again I attempted to install the ADT Plugin and on restart are faced with the non-human readable dump:

JVM terminated. Exit code=1
/usr/lib/jvm/java-7-oracle/bin/java
-Xms40m
-Xmx512m
-vm /usr/lib/jvm/java-7-oracle/bin/java
-XX:MaxPermSize=256m
-jar /home/mjseed/eclipse_classic_4.2//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar
-os linux
-ws gtk
-arch x86
-showsplash /home/mjseed/eclipse_classic_4.2//plugins/org.eclipse.platform_4.2.1.v201209141800/splash.bmp
-launcher /home/mjseed/eclipse_classic_4.2/eclipse
-name Eclipse
--launcher.library /home/mjseed/eclipse_classic_4.2//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.200.v20120522-1813/eclipse_1502.so
-startup /home/mjseed/eclipse_classic_4.2//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar
--launcher.overrideVmargs
-exitdata 4a8002
-vm /usr/lib/jvm/java-7-oracle/bin/java
-vmargs
-Xms40m
-Xmx512m
-vm /usr/lib/jvm/java-7-oracle/bin/java
-XX:MaxPermSize=256m
-jar /home/mjseed/eclipse_classic_4.2//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar

So now Eclipse doesn't even load!!

9) At this point, it is starting to try the patience of a saint. I performed the same setup of Eclipse Juno/ADT on my Win7 laptop in about 30mins and it all works fine.

10) Regarding the battery indicator, screensaver, screen brightness, etc I really do believe that Ubuntu should just be installed of certain Dell m/cs. Clearly the key developers don't want to say this but since they can't test it on all desktops/laptops then get real and prescribe certain machines that all features are known to work as required.

11) I'm keen to make the move from Windows to Ubuntu but am always faced with the same set of low-level setup issues, year after year. I see each new version of Ubuntu having UI rubbish such as hiding scrollbar thumbs, hiding main menus, "clever" ways of hiding applications in the dash etc, but what people really want is a robust system.

Well, that's my periodic moan and I just hope that someone senior reads this moan. It's back to Win7 for me where I can work on "my" tasks rather than trying to resolve Ubuntu's problems.

Till ~1 year from now when I try all of the above again.

---

### Post by MG&amp;TL on 2012-10-10
1) Developers don't read the forums, too many people whining, among other things. If you want to make a difference, speak constructively on mailing lists, and preferably offer to help.

2) [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

---

### Post by Mark Phelps on 2012-10-10
> **gmseed said:**
> ...Well, that's my periodic moan and I just hope that someone senior reads this moan. It's back to Win7 for me where I can work on "my" tasks rather than trying to resolve Ubuntu's problems.

Un fortunately, developers don't read these forums, and as far as I know, neither does Canonical; thus, although some of sympathize with your situation, it's not really going to change any.

As to using Win7, I always tell folks to use what works best for them -- and if Win7 does it for you, then unless you like the challenge of trying to get stuff to work in Ubuntu, you're really better off just using it.

---

### Post by Elfy on 2012-10-10
*Thread moved to **Ubuntu Testimonials & Experiences**.*

Use what works for you

---

### Post by Myrddin Emrys on 2012-10-10
> **gmseed said:**
> 5) It appears that by default OpenJDK is installed rather than JDK. Although Oracle's JDK runs on billions of devices Ubuntu is opting for the OpenJDL variant. To use JDK1.7_u7 I was then faced with first removing the OpenJDK. I couldn't find a software manager JDK and downloaded the latest and installed, which again could have been a lot easier.

They had no choice - Oracle has withdrawn the licence that used to allow Linux distributors to package Oracle Java:

[http://robilad.livejournal.com/90792.html](http://robilad.livejournal.com/90792.html)

---

### Post by Tamlynmac on 2012-10-10
> gmseed
It's back to Win7 for me where I can work on "my" tasks rather than trying to resolve Ubuntu's problems.
Till ~1 year from now when I try all of the above again. 	   	  	     		 	       	 		   

If you truly wish to become part of the community, then stay around and  be a part of the solution. If all you want is for others to resolve  issues (for you), then I doubt you'll ever be satisfied with  Ubuntu/Linux or any other Linux distro for that matter.


**My opinion:**
I think  these types of threads expose the agenda of some users. The implication  is: Even though Ubuntu/Linux is free, they expect it to work perfectly  without any contribution or involvement on their part. This suggests that some users really don't wish to contribute to the  community, only get something for nothing and then complain when it  doesn't meet their expectations. IMHO they should remain in the  environment that best meets said expectations, rather than corrupt the Linux  community with this entitlement mentality.

Most Linux users I  know, understand the need to contribute (basic constructive feedback,  financially supporting individual apps, etc.) and believe that their  contributions are essential to the growth of quality Linux products. Ask  yourself, am I here just because it's free and if so - why am I  complaining - if I'm "not" contributing?  :-k

Just my $0.02

---

### Post by thiebaude on 2012-10-11
+1 What can i say

---

### Post by Deer Hunter on 2012-10-11
Tamlynmac, I've seen you post things similar to this in a number of these T&E posts. You do have a valid point, but with all respect, I think there's another side to this that you may be missing.

For one thing, Windows has dominated the personal computer market for so long, so most manufacturers/software developers make their products first and foremost to be supported by Windows. This means that the for the average John Doe who buys computers with Windows pre-installed, he has come to expect (and rightfully so) that he can have support for whatever happens with his machine.

Let's say "John" does some stupid things with his computer, gets viruses, corrupts his Windows install to smithereens, and along comes some buddy who happens to be a slightly over-zealous Linux user/supporter, who tells him Windows is junk, Linux is perfect, Windows is inferior in every conceivable way, Linux never has problems, etc., and you get the point. So, John installs Linux, loves it for the first while, and then runs into a snag, but lo and behold, there's google, and there's also a forum; maybe all is not lost. However, the fixes don't always work for him, his questions don't always get answered, the total underpinnings of the OS are completely foreign from Windows, and at last he sadly reverts back to Windows thinking, "Linux sure is cool, but at I'm used to Windows and it just works."

I think this is at least part of what leads to what you are calling the agenda of certain users. I think Linux users need to be very honest with themselves, and admit that no matter how good Linux gets, it will never be perfect for everybody. Granted, some people do not spend as much time as they might to learn about it, but not everybody HAS that time; some people just want a machine that simply works to do what they want to do. And in any part of life, few things are more irritating than trying to honestly point out deficiencies/make constructive criticism, and then be told you're just complaining/whining and basically should shut up.

Personally, I make my living sitting in front of Windows 7 and it works fine. I'm careful using the internet, and I don't have problems. That being said, I have two spare laptops that I'm planning to install Ubuntu on, to see if I can make them be useful.

So what am I saying? Be honest about Linux, don't crack it up to be what it isn't, and be prepared to support and listen to those to whom you promote it.

Thanks for reading. (Gets of soapbox)

Deer Hunter

---

### Post by Bahawolf on 2012-10-12
While I run most things I need just fine in Ubuntu, I often use VMWare (before I used VirtualBox which is also fine) to use Windows in another workspace. In my particular case, it works well because with VMWare, you can use unity, and it's basically like running Windows in a window. :-) I drag and drop files into Windows as needed. It's nice!

What I was getting at, was you could try a virtual machine if you have the resources available for it. :-)

---

### Post by peethagoras on 2012-10-12
Win what? I just come back from a friend of a friend's where they run Windows XY whatever. Complained of system being slow I was not surprised. All kinds of orrible viri.

Never had virus trouble on Linux, so don't need to pay some virus-checking company every year. I would have ripped out windows and installed Lucid Lynx (which I think is quite stable and reasonably fast) if I were sure they could handle things.

Windows is designed for lazy dim wits. Although Ubunu has been going towards greater user-friendliness, Linux takes some effort and thought. (Try playing around with parallel or serial ports under Ubuntu). I got rid of all things microsofty many moons ago. Never felt the urge to return-even when my system has the odd problem - and it usually is odd.

Yes some users do expect the world to be perfect and also free, but there one has it.

---

### Post by Tamlynmac on 2012-10-12
> Deer Hunter
I think this is at least part of what leads to what you are calling the  agenda of certain users. I think Linux users need to be very honest with  themselves, and admit that no matter how good Linux gets, it will never  be perfect for everybody.

I think that's true of all  OS's - not just Linux distros. Why do Windows users even try a Linux  distro, if they believe Windows is perfect? If indeed you've read a  number of my recent posts, than you know I generally try to see both  sides of threads posted in this section. I've even been questioned (not  openly) for trying to understand the  frustrations associated with members who do post here.

Ubuntu/Linux  is free to use and yet some come here to complain that it's not good  enough. Then they make statements suggesting they'll return in the  future. Complaining about a free OS and then wondering off, seems petty  and non-productive. We should all realize that the Linux community is  based on the efforts of individuals who don't run off. I've always  believed that if one is seeking a Windows like environment, then perhaps  it's best they remain there. *My point is: That one is either part of the solution and community or their waiting  for others to put forth the effort and seek (for free) to enjoy the benefits of said efforts.*

I  could truly care less which OS someone uses. But to complain and then  say I'll be back to try again - suggests one has no desire to do  anything, other than get something for nothing at the expense of others.  Perhaps, one might wish to look up the definition of "Entitled".

How  many Linux devs work hard to produce a viable product, only to have a  user complain because they expect it to look & work just like a  Windows product they purchased. IMHO Linux users should always praise  the efforts of those who do stay around, trying to make a difference. I'd  like to take a moment and say "**THANK YOU**" to those individuals  who do step up in an effort to improve the Linux experience for users. I  can't speak for others, but please know that my family and I sincerely  appreciate your efforts. I'm aware that devs don't usually hang out  here. But, perhaps my words might inspire other Linux users to  remember that a "thank you" costs nothing, yet notifies those who participated that you appreciate all their efforts.

* Just my $0.02 and I will not post in this thread again. As this isn't a section for debate.

---

### Post by mastablasta on 2012-10-12
well i will symathize with OP. been looking for netbook or lower powered notebook working with linux. see plenty here come with no OS preloaded but none of them works with linux out of the box it seems. Ubuntu certification site is of no help as it has not been updated and only/mostly has older models not sold anymore.

same goes for users on this forum which keep saying go with this one works perfectly. that may be but it's an old model not sold anymore so statements like that are of no help at all. also latest atoms (2800, 2600) don't work well on linux i.e. no 3d support.

i have a usb key with me so cross your fingers i find something today. otherwise i guess it will be windows7 starter. the state of notebook support really seems appaling. so many models to choose from and most have at least some issues with linux.

dell with Ubuntu preloaded could be and option but it is more expencive, slightly stronger cpu means shorter batery time and also it is much heavier than the rest.

---

### Post by Erik1984 on 2012-10-13
> **mastablasta said:**
> well i will symathize with OP. been looking for netbook or lower powered notebook working with linux. see plenty here come with no OS preloaded but none of them works with linux out of the box it seems. Ubuntu certification site is of no help as it has not been updated and only/mostly has older models not sold anymore.

same goes for users on this forum which keep saying go with this one works perfectly. that may be but it's an old model not sold anymore so statements like that are of no help at all. also latest atoms (2800, 2600) don't work well on linux i.e. no 3d support.

i have a usb key with me so cross your fingers i find something today. otherwise i guess it will be windows7 starter. the state of notebook support really seems appaling. so many models to choose from and most have at least some issues with linux.

dell with Ubuntu preloaded could be and option but it is more expencive, slightly stronger cpu means shorter batery time and also it is much heavier than the rest.

Unfortunately this seems to be true. A good example are the Asus netbooks announced by [OMG!Ubuntu]("http://www.omgubuntu.co.uk/2012/06/asus-quietly-launch-new-ubuntu-netbook") . Apparently they were/are on sale in Italy... but I don't live there. My local Asus website didn't mention Ubuntu anywhere. Even if they are  for sale they are very well hidden and all those manufacturers websites have banners like "We recommend Windows 7". :(

---

### Post by nothingspecial on 2012-10-13
> This is not the place for full-scale debate or vigorous discussion, but feedback to the original poster is welcome.

In keeping with a vote by the forum membership which followed a discussion about the management of this section of the forum, threads will now be closed one week after the time of the original post. This is to allow limited discussion. No closure note will be posted to the thread. Staff may close a thread before this time if it strays from these guidelines or contravenes the forum Code of Conduct.

Closed.

---

