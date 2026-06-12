---
title: "Paint.Net Mono Jumpstart"
date: 2009-07-23
forum: The Cafe
---

### Post by keiichidono on 2009-07-23
I made a post earlier about recoding Paint.Net mono to another language but (I admit) the thread got closed because it was full of ignorance. Now that I've changed the way I view Mono (I now advocate mono when it's the best language for the job and don't advocate it when it's useless) and feel slightly important because I have a blog (check my sig) I want to try and jump start the Paint.Net mono effort. 

In a moment I'm going to send the lead programmer of Paint.Net an email asking for the source cod just for the project team (even though I need some clarification as to whether the MIT license is permissive enough or do I have to ask him to change it to GPL) so that we can get this started again. As I said on my blog, GIMP is way too cluttered and weighty to be used for average image editing. The plan to replace GIMP with F-spot is bad because F-spot doesn't have many features so if we can make Paint.Net Mono good enough, it might be up for inclusion in Karmic.

---

### Post by tqx on 2009-07-23
The code is at [http://code.google.com/p/paint-mono/source/browse/](http://code.google.com/p/paint-mono/source/browse/)

---

### Post by keiichidono on 2009-07-23
The Paint.Net mono code is there, I'm talking about the code for Paint.Net. At this point in time the source code is not released for it, and it would be extremely difficult to make a Mono port of it using out dated code.

---

### Post by directhex on 2009-07-23
> **CalvinB said:**
> I made a post earlier about recoding Paint.Net mono to another language but (I admit) the thread got closed because it was full of ignorance. Now that I've changed the way I view Mono (I now advocate mono when it's the best language for the job and don't advocate it when it's useless) and feel slightly important because I have a blog (check my sig) I want to try and jump start the Paint.Net mono effort. 

In a moment I'm going to send the lead programmer of Paint.Net an email asking for the source cod just for the project team (even though I need some clarification as to whether the MIT license is permissive enough or do I have to ask him to change it to GPL) so that we can get this started again. As I said on my blog, GIMP is way too cluttered and weighty to be used for average image editing. The plan to replace GIMP with F-spot is bad because F-spot doesn't have many features so if we can make Paint.Net Mono good enough, it might be up for inclusion in Karmic.

The MIT license is highly permissive, and that includes permission for you to relicense it to GPL if you want to.

However, I should warn you that [http://www.getpaint.net/license.html](http://www.getpaint.net/license.html) says there are Creative Commons CC-NC-ND 2.5 components - this license is not considered Free under Debian's rules, and would be a barrier to entry in Universe. You would need to replace the non-Free bits. Also worth remembering is that Paint.NET is a System.Windows.Forms application, so would both have an "alien" GUI (i.e. feel out of place in a GNOME desktop, like an app in Wine would), and is politically vexatious.

You should also feel free to contact the previous paint-mono effort, the guys behind it will be happy to answer questions (and both work on Mono upstream)

At any rate, I wish you good luck with this. As always, the Debian Mono Group are happy to help with packaging efforts, once there's something to package

---

### Post by keiichidono on 2009-07-23
> **directhex said:**
> The MIT license is highly permissive, and that includes permission for you to relicense it to GPL if you want to.

However, I should warn you that [http://www.getpaint.net/license.html](http://www.getpaint.net/license.html) says there are Creative Commons CC-NC-ND 2.5 components - this license is not considered Free under Debian's rules, and would be a barrier to entry in Universe. You would need to replace the non-Free bits. Also worth remembering is that Paint.NET is a System.Windows.Forms application, so would both have an "alien" GUI (i.e. feel out of place in a GNOME desktop, like an app in Wine would), and is politically vexatious.

You should also feel free to contact the previous paint-mono effort, the guys behind it will be happy to answer questions (and both work on Mono upstream)

At any rate, I wish you good luck with this. As always, the Debian Mono Group are happy to help with packaging efforts, once there's something to package

Thank you for that information! I would want to release it under GPL and replace the current icons with tango (compliant) icons under a more permissive CC license. I will be looking into learning C# so I can help get this started and will definitely be in contact with both groups to sort out where to begin. You seem to be very knowledgeable on this subject, is there any other way you can help me?

---

### Post by zekopeko on 2009-07-23
> **CalvinB said:**
> I made a post earlier about recoding Paint.Net mono to another language but (I admit) the thread got closed because it was full of ignorance. Now that I've changed the way I view Mono (I now advocate mono when it's the best language for the job and don't advocate it when it's useless) and feel slightly important because I have a blog (check my sig) I want to try and jump start the Paint.Net mono effort. 

In a moment I'm going to send the lead programmer of Paint.Net an email asking for the source cod just for the project team (even though I need some clarification as to whether the MIT license is permissive enough or do I have to ask him to change it to GPL) so that we can get this started again. As I said on my blog, GIMP is way too cluttered and weighty to be used for average image editing. The plan to replace GIMP with F-spot is bad because F-spot doesn't have many features so if we can make Paint.Net Mono good enough, it might be up for inclusion in Karmic.

Why didn't you just google the MIT licence?

[http://en.wikipedia.org/wiki/MIT_License](http://en.wikipedia.org/wiki/MIT_License)

It's super short.
I also don't see the reason for wanting to GPL the code since MIT is far more permissive and is also the one the Paint.net project chose.
Before you try doing that I **strongly** suggest that you read on the differences between software licences.
I'm getting the feeling that you want to GPL the project because of "group think" that all newbies that enter FLOSS contract. GPL isn't "be all and end all" licence for projects.

You would also have to rewrite the GUI to make it Gnome-ish since it will look as a Windows application.

Don't rush into this.

---

### Post by keiichidono on 2009-07-23
> **zekopeko said:**
> Why didn't you just google the MIT licence?

[http://en.wikipedia.org/wiki/MIT_License](http://en.wikipedia.org/wiki/MIT_License)

It's super short.
I also don't see the reason for wanting to GPL the code since MIT is far more permissive and is also the one the Paint.net project chose.
Before you try doing that I **strongly** suggest that you read on the differences between software licences.
I'm getting the feeling that you want to GPL the project because of "group think" that all newbies that enter FLOSS contract. GPL isn't "be all and end all" licence for projects.

You would also have to rewrite the GUI to make it Gnome-ish since it will look as a Windows application.

Don't rush into this.

Alright, I'm calming down. The idea is so awesome I almost wet myself. Ok, so I've read the wiki multiple times but I don't quite understand why it's better for the project. I like GPL because it prevents people from taking the code and going commercial with it (like what Cedega did with Wine) and the lead programmer has some big issues with that happening. If I can assure him that it will not happen I am sure he will be much happier to help us.

---

### Post by zekopeko on 2009-07-23
> **CalvinB said:**
> Alright, I'm calming down. The idea is so awesome I almost wet myself. Ok, so I've read the wiki multiple times but I don't quite understand why it's better for the project. I like GPL because it prevents people from taking the code and going commercial with it (like what Cedega did with Wine) and the lead programmer has some big issues with that happening. If I can assure him that it will not happen I am sure he will be much happier to help us.

The lead developer of what?

---

### Post by keiichidono on 2009-07-23
> **zekopeko said:**
> The lead developer of what?

Paint.Net. I found the thread while Googling, just ask if you want the link. He said he stopped sharing the source code because while it was under a different license people were stealing his code and re-branding it as their own and selling it. I can understand how he got upset over that.

---

### Post by directhex on 2009-07-23
> **CalvinB said:**
> Paint.Net. I found the thread while Googling, just ask if you want the link. He said he stopped sharing the source code because while it was under a different license people were stealing his code and re-branding it as their own and selling it. I can understand how he got upset over that.

People can still sell or rebrand GPL code - but they can't make it closed.

---

### Post by keiichidono on 2009-07-23
> **directhex said:**
> People can still sell or rebrand GPL code - but they can't make it closed.

:confused: Is there a license that doesn't permit that?

---

### Post by directhex on 2009-07-23
> **CalvinB said:**
> :confused: Is there a license that doesn't permit that?

Not an open-source one, no.

Non-commercial licenses discriminate against, well, companies. For code to be genuinely Free, it mustn't be discriminatory against ANYONE.

[http://people.debian.org/~bap/dfsg-faq.html#no_commercial](http://people.debian.org/~bap/dfsg-faq.html#no_commercial)

---

### Post by keiichidono on 2009-07-23
> **directhex said:**
> Not an open-source one, no.

Non-commercial licenses discriminate against, well, companies. For code to be genuinely Free, it mustn't be discriminatory against ANYONE.

[http://people.debian.org/~bap/dfsg-faq.html#no_commercial](http://people.debian.org/~bap/dfsg-faq.html#no_commercial)

Under the MIT license the team would not be required to release source code right? But they would have to with GPL? If so, then staying with the MIT license would be best. If it's inter-changeable then I would switch to GPL so there could be wide adoption.

---

### Post by keiichidono on 2009-07-24
After talking with someone who knows more about this and looking into it myself it doesn't say anywhere in the GPL or MIT license that anyone has to distribute the source code of the modified project but if anyone does they have to make it GPL compatible. I also need to say that a novice web designer/novice programmer alone isn't going to bring Paint.Net Mono back to life! I need some people to support me in starting it up again and when I say support I mean people actually helping me code it amongst many other things. Doesn't anyone want to see this project actually become something instead of just becoming a fading thread in the community cafe of Ubuntu Forums?

---

### Post by directhex on 2009-07-24
> **CalvinB said:**
> After talking with someone who knows more about this and looking into it myself it doesn't say anywhere in the GPL or MIT license that anyone has to distribute the source code of the modified project but if anyone does they have to make it GPL compatible.

If you distribute a binary compiled from MIT code, you can keep the code

If you distribute a binary compiled from GPL code, you must offer your code due to the GPL.

---

### Post by zekopeko on 2009-07-24
> **CalvinB said:**
> Paint.Net. I found the thread while Googling, just ask if you want the link. He said he stopped sharing the source code because while it was under a different license people were stealing his code and re-branding it as their own and selling it. I can understand how he got upset over that.

Link, please.

The question remains why would you licences your software under MIT if you don't want people to use your code without contributing.

---

### Post by keiichidono on 2009-07-24
> **zekopeko said:**
> Link, please.

The question remains why would you licences your software under MIT if you don't want people to use your code without contributing.

[http://paintdotnet.forumer.com/viewtopic.php?f=12&t=26836](http://paintdotnet.forumer.com/viewtopic.php?f=12&t=26836)

[http://paintdotnet.forumer.com/viewtopic.php?f=27&t=28275](http://paintdotnet.forumer.com/viewtopic.php?f=27&t=28275)

I'm just going to give up on this. It would require me putting in a lot of hours re-programming Paint.Net by myself and I don't know if the developer will be so kind as to give me the current source code and if he does not then i'll be stuck with old source code. Not to mention porting it in the first place would be quite hard and I could only support x86 and Gnome since that's what I use. KDE and x64 would be left out. I just don't think it's worth it if no one else thinks it's worth it to help me out.

---

### Post by bryonak on 2009-07-25
> **CalvinB said:**
> 
I'm just going to give up on this. It would require me putting in a lot of hours re-programming Paint.Net by myself and I don't know if the developer will be so kind as to give me the current source code and if he does not then i'll be stuck with old source code.

Don't listen to the grumpy naysayers, there are such people in every community.
The GPL might help preventing what happened to this dev, so try to ask him politely.


> **CalvinB said:**
> Not to mention porting it in the first place would be quite hard and I could only support x86 and Gnome since that's what I use.

> **Linus Torvalds about the kernel, 1991]
It is NOT protable (uses 386 task switching etc), and it probably never
  will support anything other than AT-harddisks, as that's all I have :-(.
[/QUOTE]

The point is that Linus actually started to produce code *before* people with different hardware started helping him out.


[QUOTE=CalvinB said:**
> I just don't think it's worth it if no one else thinks it's worth it to help me out.
You often have to be motivated enough to pull your project off by yourself for the first few months.
When people realise it's useful/cool/awesome, you'll have lots of support quickly.
Yet at the moment, why should one invest his time in a hazy idea instead of contributing to an already successful FOSS project like GIMP?

---

