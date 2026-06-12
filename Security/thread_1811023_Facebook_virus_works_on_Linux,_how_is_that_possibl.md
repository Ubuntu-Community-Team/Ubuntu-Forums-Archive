---
title: "Facebook virus works on Linux, how is that possible?"
date: 2011-07-24
forum: Security
---

### Post by peterballard on 2011-07-24
So one of my friends had a facebook wall post: "Crazy idiot. He almost killed her. Dad Drops His Daughter to Try to Catch a Baseball on LIVE TV!" with a link to the video. I foolishly didn't notice the video was not youtube or any other reputable site and clicked the link. I clicked to my home page, and it asked "are you sure" (or words to that effect), I answered yes (possibly foolishly again).

A few minutes later (or maybe immediately) the same post came up on my wall. For the first time in 14 years using Linux, I've propagated some sort of virus. Ouch!

So how did this work? My guess is clicking the link enabled some sort of Javascript program. Does anyone know if that is correct?

I rebooted, deleted all my history/cache/cookies, and changed my Facebook password. Does that make it secure?

Optional bonus question: what do I advise my Windows-using friends to do?

---

### Post by handy on 2011-07-24
So many people have caught "The Facebook Virus". It is just an unfortunate & sad sign of the times.

There are a couple of ways to protect yourself, one is obvious the other I'll leave for someone else to post...

[edit:] This may be of some use to you:

[http://www.bloggingbasics101.com/2011/05/how-do-i-get-rid-of-a-facebook-virus/](http://www.bloggingbasics101.com/2011/05/how-do-i-get-rid-of-a-facebook-virus/)

---

### Post by hakermania on 2011-07-24
Read my signature.
It is not at all impossible for linux to catch a virus. I myself have made some viruses for linux but I have not spread them, only to prove that they can exist for the non-believers. On the other hand USB control (there's no auto-execute in Linux) and sudo password provides you with <more than enough> security...!
As for your case, I don't know much about internet HTML javascript etc but I suspect that it hijacked your cookies and send them to other PC which made the posts from your accouunt or this was made directly from your PC. It's only an assumption :/

---

### Post by peterballard on 2011-07-24
Thanks for both answers. (I followed the instructions from Handy's link, but there was nothing hostile in my list of facebook apps). But I'm still puzzled about the mechanism.

I realise a virus can run on Linux (or any other operating system). But how can it be started from a single web site visit? I thought HTML/Javascript didn't allow programs to "escape" the browser.

How would hijacking cookies help? If passwords were stored in cookies then a web site can read them, but that is such an obvious security hole it'd be a pretty stupid website which allowed that.

And if the password can't be got from cookies, where else can it get them from? Directly from facebook? (If so, I'm less concerned, because that would make it a facebook-specific security hole).

---

### Post by hakermania on 2011-07-24
> **peterballard said:**
> Thanks for both answers. (I followed the instructions from Handy's link, but there was nothing hostile in my list of facebook apps). But I'm still puzzled about the mechanism.

I realise a virus can run on Linux (or any other operating system). But how can it be started from a single web site visit? I thought HTML/Javascript didn't allow programs to "escape" the browser.

How would hijacking cookies help? If passwords were stored in cookies then a web site can read them, but that is such an obvious security hole it'd be a pretty stupid website which allowed that.

And if the password can't be got from cookies, where else can it get them from? Directly from facebook? (If so, I'm less concerned, because that would make it a facebook-specific security hole).
Well, for example, if you login to facebook you get a cookie that facebooks checks every time to see if you have. This cookie grants you access to your facebook account. If someone  hijacks this cookie he has instant access to your account **but not your password**.
Also, I repeat that it was only an assumption.

---

### Post by haqking on 2011-07-24
it seems more of a facebook specific issue here, more of a XSS vulnerability than a virus on your Linux System.

---

### Post by nrundy on 2011-07-24
> **hakermania said:**
> Read my signature.
It is not at all impossible for linux to catch a virus. I myself have made some viruses for linux but I have not spread them, only to prove that they can exist for the non-believers. On the other hand USB control (there's no auto-execute in Linux) and sudo password provides you with <more than enough> security...!
As for your case, I don't know much about internet HTML javascript etc but I suspect that it hijacked your cookies and send them to other PC which made the posts from your accouunt or this was made directly from your PC. It's only an assumption :/

What do you mean: "On the other hand USB control . . ."?
One of the things that annoys me is that everytime I copy something from a USB onto my ext4 hard drive it lands with executable capabilities. I always have to manually remove exe from permissions when I copy a file over.

---

### Post by nrundy on 2011-07-24
> **peterballard said:**
> So one of my friends had a facebook wall post: "Crazy idiot. He almost killed her. Dad Drops His Daughter to Try to Catch a Baseball on LIVE TV!" with a link to the video. I foolishly didn't notice the video was not youtube or any other reputable site and clicked the link. I clicked to my home page, and it asked "are you sure" (or words to that effect), I answered yes (possibly foolishly again).

A few minutes later (or maybe immediately) the same post came up on my wall. For the first time in 14 years using Linux, I've propagated some sort of virus. Ouch!

So how did this work? My guess is clicking the link enabled some sort of Javascript program. Does anyone know if that is correct?

I rebooted, deleted all my history/cache/cookies, and changed my Facebook password. Does that make it secure?

Optional bonus question: what do I advise my Windows-using friends to do?

PeterBallard, just out of curiosity what web browser are you using? Chrome, Firefox? Do you use NoScript, was it allowing everything on the page, just Facebook?

I wonder if Internet Explorer 9 would have alerted you to the danger before you clicked the infected link? I've been reading and hearing about how effective IE9 is at preventing this: [http://www.ghacks.net/2011/07/16/ie9-decimates-other-browsers-for-socially-engineered-malware-protection/](http://www.ghacks.net/2011/07/16/ie9-decimates-other-browsers-for-socially-engineered-malware-protection/)

---

### Post by wacky_sung on 2011-07-24
I do not know how much a facebook virus / malware can affect Ubuntu.I have been clicking on countless facebook virus / malware links from my facebook friends posting and it got no impact at all. I currently running through privoxy -> ziproxy -> squid proxy -> browser.By the time, i click on it and it have totally no effect at all.I will appreciate if you can send me the link and i bet 99% it got no impact even it run on exploits / vulnerability to plant a virus/malware on me.:guitar:

---

### Post by Dangertux on 2011-07-24
Haqking is once again right on the money.

This "virus" did nothing to your computer , nor is it a virus. It exploited what isn't even really an unintentional vulnerability in Facebook (but should still be removed). Where a javascript can utilize the credentials you've already used to login with (note the cookie mentioned previously)

To post something on your wall.

---

### Post by Maikl on 2011-07-24
Total newby to Linux here, and I don't use Facebook, but drawing on experience from Windows I'd say this is a Facebook issue, not malware on your pc. There's loads of scams running on Facebook, if you read through some of the FB-related articles on the _[COLOR=Blue][Sophos blog]("http://nakedsecurity.sophos.com/")[/COLOR]_ you'll get an idea of how these things circulate.

_[COLOR=Blue][NoScript for Firefox]("https://addons.mozilla.org/en-US/firefox/addon/noscript/")[/COLOR]_ will protect your browser (if its Firefox) against scripts, you might also like [COLOR=Black]_[BetterPrivacy]("https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/")_.[/COLOR]

---

### Post by nrundy on 2011-07-24
I've been looking but can't find the article. There was not too long ago a vulnerability in facebook that compromised people's tokens i think. I think wat u experienced was a facebook vulnerability.

Facebook is really crap IMHO. I deleted my account long time ago. Personally, I hope facebook dies off and people totally stop using it. Hopefully Google+ will facilitate this.

---

### Post by Thewhistlingwind on 2011-07-24
I have a webpage around here somewhere that I show as an example to tell people why noscript is important.

It's basically a piece of cross-platform javascript voodoo that posts stuff to someones wall/hijacks their account. (The exploit, not the webpage, the webpage just has the source code.)

---

### Post by bodhi.zazen on 2011-07-24
First, not every piece of malware is a "virus".

Second, yes there are cross platform vulnerabilities for browsers, at a minimum use NoScript.

If you are further interested learn to use apparmor.

---

### Post by uRock on 2011-07-24
That code attacks FB's systems, not your's. 

You clicked a button and though it didn't say it was going to repost, it did. 

I have watched many people fall for these schemes. To me they are obvious, because the people who fall for them don't usually post videos or any other links.

---

### Post by peterballard on 2011-07-25
Thanks for all the replies so far. I am running Ubuntu/8.04, Firefox/3.0.15. Yes I realised it might not technically be a "virus" but when I don't know what it is it's unclear what word to use :)

It doesn't appear to have taken my password (as suggested by the link from the first reply). I changed my password back to what it was when I had the problem (which is safe enough because I'm not silly enough give Facebook sensitive information like my real birthdate), and there have been no rogue posts. 

So the suggestions that it ran something on Facebook (rather than my PC) seem correct. It appears to simply treat clicking the link as nothing more than authority to repost itself on my Facebook wall (at least on Linux).

wacky_sung asked for the URL of the link, but I can't find it now. Sorry. If you google the phrase I put in my first post, i.e. "crazy idiot he almost killed her" (with quotes) there are a few hits which might be it.

---

### Post by uRock on 2011-07-25
> **peterballard said:**
> wacky_sung asked for the URL of the link, but I can't find it now. Sorry. If you google the phrase I put in my first post, i.e. "crazy idiot he almost killed her" (with quotes) there are a few hits which might be it.

I think the FB team cleaned it up. My wall was riddled with posts by others who clicked the "spider under the skin" link the other day. :D

---

### Post by Chayak on 2011-07-25
> **bodhi.zazen said:**
> First, not every piece of malware is a "virus".

Second, yes there are cross platform vulnerabilities for browsers, at a minimum use NoScript.

If you are further interested learn to use apparmor.

+1

It wasn't a virus. It was a cross site scripting exploit.

There was a talk at Blackhat 2006 on a javascript resident implant (what's generally called a virus or spyware) that stayed resident in the browser and could, at the time, access the file system of the host.  The vulnerability it used has since been patched but it shows you what can be done with some imagination and skill.

Moral of the story is: Use NoScript and only allow essential scripts from the site you're visiting to be run.

With Windows 8 focusing on HTML5 and Javascript as a primary language expect to see more Javascript based malware that could easily be made cross platform.

Here's the link to the briefing.
Warning PDF
[http://www.blackhat.com/presentations/bh-jp-06/BH-JP-06-Grossman.pdf]("http://www.blackhat.com/presentations/bh-jp-06/BH-JP-06-Grossman.pdf")

---

### Post by c.cobb on 2011-07-26
> **Dangertux said:**
> This "virus" did nothing to your computer , nor is it a virus. It exploited what isn't even really an unintentional vulnerability in Facebook (but should still be removed). Where a javascript can utilize the credentials you've already used to login with (note the cookie mentioned previously)

FaceBook doesn't use the HttpOnly flag? Unbelievable. As Mr. Grossman mentions in the presentation that Chayak linked to, "...implement HttpOnly. It's been around for years!" And that was back in 2006. Yet another Epic Fail for FB.

---

### Post by wacky_sung on 2011-07-27
> **peterballard said:**
> Thanks for all the replies so far. I am running Ubuntu/8.04, Firefox/3.0.15. Yes I realised it might not technically be a "virus" but when I don't know what it is it's unclear what word to use :)

It doesn't appear to have taken my password (as suggested by the link from the first reply). I changed my password back to what it was when I had the problem (which is safe enough because I'm not silly enough give Facebook sensitive information like my real birthdate), and there have been no rogue posts. 

So the suggestions that it ran something on Facebook (rather than my PC) seem correct. It appears to simply treat clicking the link as nothing more than authority to repost itself on my Facebook wall (at least on Linux).

wacky_sung asked for the URL of the link, but I can't find it now. Sorry. If you google the phrase I put in my first post, i.e. "crazy idiot he almost killed her" (with quotes) there are a few hits which might be it.

I will suggest you to upgrade your Ubuntu to the latest version so that bugs are fixed. Beside that, i have already tested with countless facebook hoax which has no effect on my Ubuntu system. Whatsoever attacks they has carried mostly pointing to the browser vulnerability such as using java script, cross sites script attack,cookies, etc but most of those attacks are often easily being filter out by Privoxy and Proxy servers.You can actually view the the source code(script) of the attackers and understand how the attack being carried out.

---

### Post by salemeni on 2011-08-04
Hi
You can scan your PC with antivirus.

[http://www.clamav.net/](http://www.clamav.net/)

[http://www.avast.com/fre/avast-for-GNU/Linux-workstation.html](http://www.avast.com/fre/avast-for-GNU/Linux-workstation.html)
[http://www.sophos.fr/products/enterprise/endpoint/security-and-control/GNU/Linux/](http://www.sophos.fr/products/enterprise/endpoint/security-and-control/GNU/Linux/)
[http://www.pandasoftware.com/download/GNU/Linux/GNU/Linux.asp](http://www.pandasoftware.com/download/GNU/Linux/GNU/Linux.asp)
[http://download.avgfree.com/filedir/inst/avg85flx-r732-a3168.i386.tar.gz](http://download.avgfree.com/filedir/inst/avg85flx-r732-a3168.i386.tar.gz)
[http://www.eset.com/us/business/server-security/linux-file](http://www.eset.com/us/business/server-security/linux-file)
and more ...
Thanks

---

### Post by haqking on 2011-08-04
> **salemeni said:**
> Hi
You can scan your PC with antivirus.

[http://www.clamav.net/](http://www.clamav.net/)

[http://www.avast.com/fre/avast-for-GNU/Linux-workstation.html](http://www.avast.com/fre/avast-for-GNU/Linux-workstation.html)
[http://www.sophos.fr/products/enterprise/endpoint/security-and-control/GNU/Linux/](http://www.sophos.fr/products/enterprise/endpoint/security-and-control/GNU/Linux/)
[http://www.pandasoftware.com/download/GNU/Linux/GNU/Linux.asp](http://www.pandasoftware.com/download/GNU/Linux/GNU/Linux.asp)
[http://download.avgfree.com/filedir/inst/avg85flx-r732-a3168.i386.tar.gz](http://download.avgfree.com/filedir/inst/avg85flx-r732-a3168.i386.tar.gz)
[http://www.eset.com/us/business/server-security/linux-file](http://www.eset.com/us/business/server-security/linux-file)
and more ...
Thanks


this has already been established as a XSS flaw and not a virus.

Also all your links are broken except for clamv and eset ;-)

---

### Post by 2Stoned on 2011-08-11
I use Firefox addons to prevent harmfull javascript or other active components on websites, it will block the components when the page loads, you can use NoScript addon and choose for yourself to activate them when you are sure its safe. Another addon i use is LinkExtend.

---

### Post by nec207 on 2011-08-11
> **peterballard said:**
> So one of my friends had a facebook wall post: "Crazy idiot. He almost killed her. Dad Drops His Daughter to Try to Catch a Baseball on LIVE TV!" with a link to the video. I foolishly didn't notice the video was not youtube or any other reputable site and clicked the link. I clicked to my home page, and it asked "are you sure" (or words to that effect), I answered yes (possibly foolishly again).
 
A few minutes later (or maybe immediately) the same post came up on my wall. For the first time in 14 years using Linux, I've propagated some sort of virus. Ouch!
 
So how did this work? My guess is clicking the link enabled some sort of Javascript program. Does anyone know if that is correct?
 
I rebooted, deleted all my history/cache/cookies, and changed my Facebook password. Does that make it secure?
 
Optional bonus question: what do I advise my Windows-using friends to do?
 
 
Yes there was some virus that Linux and Mac computers got and spread to other computers.So much for the myth of Linux and Mac computers do not get virus.
 
It was on facebook of Bin Ladens death the user would click on the link or pop up than click and get the virus.
 
 
[http://www.cfnews13.com/article/news/2011/may/239142/Cybercriminals-use-bin-Ladens-death-to-trick-you-on-Facebook-Google](http://www.cfnews13.com/article/news/2011/may/239142/Cybercriminals-use-bin-Ladens-death-to-trick-you-on-Facebook-Google)

---

### Post by nec207 on 2011-08-11
> **peterballard said:**
> Thanks for both answers. (I followed the instructions from Handy's link, but there was nothing hostile in my list of facebook apps). But I'm still puzzled about the mechanism.
 
I realise a virus can run on Linux (or any other operating system). But how can it be started from a single web site visit? I thought HTML/Javascript didn't allow programs to "escape" the browser.
 
How would hijacking cookies help? If passwords were stored in cookies then a web site can read them, but that is such an obvious security hole it'd be a pretty stupid website which allowed that.
 
And if the password can't be got from cookies, where else can it get them from? Directly from facebook? (If so, I'm less concerned, because that would make it a facebook-specific security hole).
 
 
I think like poster was saying it hijack your cookie .It does not make sense I can see flash doing this but not Javascrip.
 
Well Javascript runs on the page but not flash needs connection to OS.

---

### Post by uRock on 2011-08-11
> **nec207 said:**
> Yes there was some virus that Linux and Mac computers got and spread to other computers.So much for the myth of Linux and Mac computers do not get virus.
 
It was on facebook of Bin Ladens death the user would click on the link or pop up than click and get the virus.
 
 
[http://www.cfnews13.com/article/news/2011/may/239142/Cybercriminals-use-bin-Ladens-death-to-trick-you-on-Facebook-Google](http://www.cfnews13.com/article/news/2011/may/239142/Cybercriminals-use-bin-Ladens-death-to-trick-you-on-Facebook-Google)

Your article says nothing about a Linux virus. Please do not spread FUD.

---

### Post by nec207 on 2011-08-13
> **uRock said:**
> Your article says nothing about a Linux virus. Please do not spread FUD.
 
 
It was much like what OP was saying  here it got spread by clicking on lick or pop up and spread to the other people facebook.
 
Do to Linux or OS X it probably did not do anything to the OS do to it was program to go after windows OS.

---

### Post by clanky on 2011-08-15
> **peterballard said:**
>  and it asked "are you sure" (or words to that effect), I answered yes (possibly foolishly again).

The "words to that effect" would actually have been something along the lines of :

<application> is requesting permission to:
Access my basic information
Includes name, profile picture, gender, networks, user ID, list of friends and any other information I've shared with everyone.

This is exactly why no desktop system is immune to malware, in this case all it did was ask to repost some garbage on your wall, but the point is that you allowed a webpage to do something that you didn't want it to do and no matter what operating system you are running if you click yes enough times the operating system will let you break it.

Linus is arguably a more secure server OS than others, but no operating system can protect a desktop OS from the idiot behind the keyboard. 

More and more malware relies on social engineering than on software engineering and as Linux becomes more popular there will be more and more users without the common sense to not click on the "free prOn here" links and more and more people will end up with borked systems, we can only hope that the people making the virusses can't keep up with the ever changing goalposts for writing workable Linux software.

---

### Post by nec207 on 2011-08-15
>  
This is exactly why no desktop system is immune to malware, in this case all it did was ask to repost some garbage on your wall, but the point is that you allowed a webpage to do something that you didn't want it to do and no matter what operating system you are running if you click yes enough times the operating system will let you break it.

 
On windows I can see that happing but how can Linux or OS X allow this to happen.If you click on it well nothing should happen.
 
-  1 the OS is more secure 
-  2 The programmers would have to write code for Linux or OS X.
-  3 Facebook should not allow code to just run.
-  4 And alot more.

---

### Post by haqking on 2011-08-15
> **nec207 said:**
> On windows I can see that happing but how can Linux or OS X allow this to happen.If you click on it well nothing should happen.
 
-  1 the OS is more secure 
-  2 The programmers would have to write code for Linux or OS X.
-  3 Facebook should not allow code to just run.
-  4 And alot more.

1. Linux is more secure out of the box but browing the internet and running scripts is a bit different.
2. no, Browser scripts are often OS agnostic
3. Facebook should not do alot of things
4. .....

The title of this thread is wrong as it states Facebook virus.  What the OP was referring to was not a virus but XSS or cross site scripting error.

This happens in a browser, again Security 101 comes into play, dont do things unless you are sure you want to, least privelege etc.

Use things like Noscript in firefox......etc

---

### Post by nec207 on 2011-08-15
> . Linux is more secure out of the box but browing the internet and running scripts is a bit different.
 
Where was the browser sanbox?
>  
 
2. no, Browser scripts are OS agnostic

 
What do you mean?
 
 >  

3. Facebook should not do alot of things
 
 
Than thats ban flash,java ,java scrip and active-x.All are roads open for malware.
>  
 
 
 
 
The title of this thread is wrong as it states Facebook virus. What the OP was referring to was not a virus but XSS or cross site scripting error.

 
It funny it did not put a trojen on his computer.
 
>  
This happens in a browser, again Security 101 comes into play, dont do things unless you are sure you want to, least privelege etc.
 
Use things like Noscript in firefox......etc

 
True but OS and browsers should just run bad code.

---

### Post by bodhi.zazen on 2011-08-15
As indicated earlier, both apparmor and selinux will help.

BUT, firefox has many vulnerabilities. Just check this page for xulrunner or firefox.

---

### Post by bodhi.zazen on 2011-08-15
> **nec207 said:**
> Where was the browser sanbox?

You mean sandbox ? You keep asking the same question and I keep giving you the dame answer.

[here it is](http://blog.bodhizazen.net/linux/selinux-sandbox/)

That link was also on Planet Ubuntu.

For Ubuntu, use apparmor.

---

### Post by nec207 on 2011-08-17
> **bodhi.zazen said:**
> You mean sandbox ? You keep asking the same question and I keep giving you the dame answer.
 
[here it is]("http://blog.bodhizazen.net/linux/selinux-sandbox/")
 
That link was also on Planet Ubuntu.
 
For Ubuntu, use apparmor.
 
sorry I was replying to haqking I should have quoted his post better.
 
 
My spelling was of too and that did not help.

---

### Post by Dangertux on 2011-08-17
> **c.cobb said:**
> FaceBook doesn't use the HttpOnly flag? Unbelievable. As Mr. Grossman mentions in the presentation that Chayak linked to, "...implement HttpOnly. It's been around for years!" And that was back in 2006. Yet another Epic Fail for FB.


Wow this is still going cool. 

Anyways sorry I didn't respond earlier kinda been away for awhile.  Yes FB could fix this, however if you note in my original post I said it wasn't unintentional. That wasn't a typo, Facebook loves to share your information with other sites, you know you visit a site and it magically can tell you that your friends "like" it lol.

Unforunately this can be used for a lot of things, some annoying, some good, and many bad.  Gotta watch out for those folks who want you to "Help their Farm" ;-)

---

### Post by cprofitt on 2011-08-18
Question for the OP:

Sorry if this was answered earlier... I browsed the thread, but did not see it asked.

Were you at home or on a public wi-fi network?

---

### Post by Snowboi on 2011-08-19
> it seems more of a facebook specific issue here, more of a XSS vulnerability than a virus on your Linux System.

+ 1 not a linux vulnerability but a facebook vulnerability.

---

### Post by uRock on 2011-08-19
> **Snowboi said:**
> + 1 not a linux vulnerability but a facebook vulnerability.

Yup. :D

This thread has been answered time and again,

Thread Closed.

---

