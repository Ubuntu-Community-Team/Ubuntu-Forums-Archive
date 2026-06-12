---
title: "Licence Question"
date: 2008-11-27
forum: The Cafe
---

### Post by kineem on 2008-11-27
I have coded a program and will release soon. I respect open source philosophy and want to use its opportunies by releasing the program with GPL. But there is a possiblity I might sell the program to a company in future. In that case the company high probably willnt want to buy  GPL licenced program. So there are some questions I want to ask. 

1. If I release the program with GPL, in future can I revert the licence back to a copyright licence?

2. Is there a licence suitable for a program which tries to use the open source oppurtunies but can be sold to a company?

Thanks.

---

### Post by Ozor Mox on 2008-11-27
> 1. If I release the program with GPL, in future can I revert the licence back to a copyright licence?

Since you are the copyright holder, you are able to change the licence of your program. All previous versions of it will remain under the GPL however.

> 2. Is there a licence suitable for a program which tries to use the open source oppurtunies but can be sold to a company?

I'm almost positive these do exist. Have a look [here](http://en.wikipedia.org/wiki/List_of_FSF_approved_software_licences) and [here](http://en.wikipedia.org/wiki/List_of_OSI_approved_software_licences).

---

### Post by mihai.ile on 2008-11-27
Well I hade the same problem whan I made jKiwi ([www.jkiwi.com](www.jkiwi.com)) I wanted to be GPL and also wanted to sell it to a hairstyler!
So this is how I did it ad I succeeded:
released the application gpl and told him it's free.
what he payd was for the hairstyles that the application has installed, build only for him and not available for free over the net.
This way everybody wins.
He payd for customizing a software to his needs (a personal version) while the software is available under GPL.

But of course it depends from case to case, what does your software do?

---

### Post by kamitsukai on 2008-11-27
erm at question one how could that possibley work? as the point of open source is that people can change an adjust any work under an open source licence and even include it in there own, so if suddenly changed the licence then how would this effect there work...

---

### Post by balaknair on 2008-11-27
> **kamitsukai said:**
> erm at question one how could that possibley work? as the point of open source is that people can change an adjust any work under an open source licence and even include it in there own, so if suddenly changed the licence then how would this effect there work...

I think it would go something like this-
Let's say versions 1, 2, and 3 of an app were released under the GPL, but at version 4 the developer(who holds the copyright since he released it under the GPL) decides to use a different license(and maybe makes it a closed source product), he has every right to do so. Versions 1, 2 and 3 will remain open source and under the GPL, but versions 4 and later will be under the new license the developer has chosen. Others are still free to use code from the first 3 versions(GPL) and use it as they please(and maybe fork the project?), but not version 4.

I think one example of this is the Cobian backup tool, where version 8 was open source(Mozilla Public License), but at version 9 it is now a closed source project. You can still study/use/modify the code in version 8, but not version 9.

[http://www.educ.umu.se/~cobian/cobianbackup.htm#OS](http://www.educ.umu.se/~cobian/cobianbackup.htm#OS)

---

### Post by aysiu on 2008-11-27
> **mihai007 said:**
> Well I hade the same problem whan I made jKiwi ([www.jkiwi.com](www.jkiwi.com)) I wanted to be GPL and also wanted to sell it to a hairstyler!
So this is how I did it ad I succeeded:
released the application gpl and told him it's free.
what he payd was for the hairstyles that the application has installed, build only for him and not available for free over the net.
This way everybody wins.
He payd for customizing a software to his needs (a personal version) while the software is available under GPL.

But of course it depends from case to case, what does your software do?
GPL'ed software is often given away free, but the GPL also allows you to sell it.

---

### Post by Ozor Mox on 2008-11-27
> **aysiu said:**
> GPL'ed software is often given away free, but the GPL also allows you to sell it.

It's a nice idea, but the trouble with it in the real world is that as soon as any individual/company finds out the code is freely available, they will know that they don't have to pay for it. They might even feel ripped off if they paid for it when they could have got it for free. This seems to be why most GPL software is given away free or relies on donations. It's unfortunate, but it's the way the world works, and something I think RMS still seems to be blissfully unaware of :)

---

### Post by aysiu on 2008-11-27
> **Ozor Mox said:**
> It's a nice idea, but the trouble with it in the real world is that as soon as any individual/company finds out the code is freely available, they will know that they don't have to pay for it. They might even feel ripped off if they paid for it when they could have got it for free. This seems to be why most GPL software is given away free or relies on donations. It's unfortunate, but it's the way the world works, and something I think RMS still seems to be blissfully unaware of :)
I know. I just wanted to let mihai007 know there's no need to do all those mental backflips to get around the GPL. The GPL allows you to sell software. Is it practical to sell it for a lot? No. But it is possible and fully in compliance with the license.

---

### Post by Ozor Mox on 2008-11-27
> **aysiu said:**
> I know. I just wanted to let mihai007 know there's no need to do all those mental backflips to get around the GPL. The GPL allows you to sell software. Is it practical to sell it for a lot? No. But it is possible and fully in compliance with the license.

True. I suppose the value from GPL software comes more from services you can provide with it, or from customising it to the specific needs of a customer, than actually selling it.

---

### Post by koenn on 2008-11-27
> **Ozor Mox said:**
> It's a nice idea, but the trouble with it in the real world is that as soon as any individual/company finds out the code is freely available, they will know that they don't have to pay for it. They might even feel ripped off if they paid for it when they could have got it for free. 
Even when the source is freely available, you're customer still needs binaries, so unless he's going to compile it himself (and compile all subsequent updates, patches, ...) he might still be interested in actually buying a compiled program with a sensible default configuration rather than a bag of source files.  That would work untill someone starts distributing binaries for free at a reasonably large scale. There's nothing in the GPL that would force anyone to do this, though it is allowed.

> **Ozor Mox said:**
>  It's unfortunate, but it's the way the world works, and something I think RMS still seems to be blissfully unaware of :)
Seeing that there's a whole article on selling GPL'd software on the GNU (or FSF ?) website, I'd guess RMS isn't blissfully unaware of anything of the sort.

---

### Post by Ozor Mox on 2008-11-27
> Seeing that there's a whole article on selling GPL'd software on the GNU (or FSF ?) website, I'd guess RMS isn't blissfully unaware of anything of the sort.

Yeah I have read through that article. I more meant that he seems to be unwilling to explain how software developers would ever make any money if *all* software were free-as-in-freedom. I don't have a link to it now, but I listened to a podcast thing where someone asked him this question and he kept saying that they would have to get another job if they could not earn a living writing software. I thought, yeah great, so now we have no software developers...good one!

Seriously, I actually really respect RMS's view, but there are some things on the commercial side of free software that I still find hard to understand.

---

### Post by koenn on 2008-11-27
> **Ozor Mox said:**
> 
Seriously, I actually really respect RMS's view, but there are some things on the commercial side of free software that I still find hard to understand.
Eric Raymond, in The Magic Cauldron, looks at the economics of open source and describes some 'business models' for open source. It's on the web.

The most common approach is to give away the software but sell services related to it (user support, service level agreements, customization, consultancy, ...)

An other way is what i said before : sell binaries, and give the source with it. 

Yet an other scenario is the case of software made to order. Say I (or my company) orders some software to be written to suit a specific need. Say we'd be interested in also having the source code, to avoid vendor lock-in or dependency on the programmer, and obtain the right to redistribute the software, either as-is or modified. If the software is not of strategic importance to our business (or assume we're a not-for profit organization), probably we wouldn't mind others using it too so we can sell it to them or give it away. So actually, the program would be open source/free software, but the programmer still got payed for it. 

One last scenario : lots of big IT companies have employees contributing to open source projects : IBM, Oracle, ... probably Google too, and there might be a few lesser knowns as well (eg manufacturers of appliances with embedded open source software ),  ...
They do this for business reasons, like : they use open source themselves or sell a product that uses or is based on open source code, they want it improved or adapted because it makes business sense, so they have their personel produce the improvements, and because the software is open source, the modifications are open source as well (in the case of GPL and similar licenses)

So open source doesn't equal starving coders.

---

### Post by kineem on 2008-11-27
> **balaknair said:**
> I think it would go something like this-
Let's say versions 1, 2, and 3 of an app were released under the GPL, but at version 4 the developer(who holds the copyright since he released it under the GPL) decides to use a different license(and maybe makes it a closed source product), he has every right to do so. Versions 1, 2 and 3 will remain open source and under the GPL, but versions 4 and later will be under the new license the developer has chosen. Others are still free to use code from the first 3 versions(GPL) and use it as they please(and maybe fork the project?), but not version 4.

I think one example of this is the Cobian backup tool, where version 8 was open source(Mozilla Public License), but at version 9 it is now a closed source project. You can still study/use/modify the code in version 8, but not version 9.

[http://www.educ.umu.se/~cobian/cobianbackup.htm#OS](http://www.educ.umu.se/~cobian/cobianbackup.htm#OS)

Thanks for all replies. Has Cobian 9 completely  use different source  code than Cobian 8 becuase of "closed source projects cant use open source code fact"? 

Now let me clear some things. My software will generate income according to my estimates. Now I can completely release it as GPL to be able to use those wonderful GPL programming libraries. But the problem is, if I release the software with GPL then whole code becomes GPL'd and some other guys may grab it, rename it, use it and generate income from it. That isnt problem for me but If I come to sell the software to a company, the company may not want others to generate income from the software. Another problem as balaknair said switching open to close cant actually close the software. So for my case I think GPL isnt for me. But I still seek a way that will allow me use open source libraries or contributions. I dont want the release the software as close licensed but the possibility of selling the program to a company will lead me to do so, right?

---

### Post by koenn on 2008-11-27
> **kineem said:**
> 
if I release the software with GPL then whole code becomes GPL'd and some other guys may grab it, rename it, use it and generate income from it.
Wouldn't those other guys have the same problem you have : how do I make money of open source ?

> **kineem said:**
> 
I dont want the release the software as close licensed but the possibility of selling the program to a company will lead me to do so, right?
I don't see how you come to this conclusion.
I don't know who your prospective customer is, but if the software is important enough for them to justify paying for it, why wouldn't they pay for it ? 
And what reason do you think they have to object to the fact that others might be using that software too ? Or selling it ?  And why would they care whether these others payed for it or not, or how much they payed, if anything. What difference could that possibly make ?

---

### Post by kineem on 2008-11-27
> **koenn said:**
> Wouldn't those other guys have the same problem you have : how do I make money of open source ?


I don't see how you come to this conclusion.
I don't know who your prospective customer is, but if the software is important enough for them to justify paying for it, why wouldn't they pay for it ? 
And what reason do you think they have to object to the fact that others might be using that software too ? Or selling it ?  And why would they care whether these others payed for it or not, or how much they payed, if anything. What difference could that possibly make ?
I dont actually know much about how companies behave or think. But I thought they would prefer the licence type which let them get all the income and prevent making others benefiting from software.

---

### Post by koenn on 2008-11-27
> **kineem said:**
> I dont actually know much about how companies behave or think. But I thought they would prefer the licence type which let them get all the income and prevent making others benefiting from software.
ah, you're thinking of selling it to a company for them to resell it ?

---

### Post by kineem on 2008-11-27
> **koenn said:**
> ah, you're thinking of selling it to a company for them to resell it ?

yes

---

### Post by Slug71 on 2008-11-27
> **mihai007 said:**
> Well I hade the same problem whan I made jKiwi ([www.jkiwi.com](www.jkiwi.com)) I wanted to be GPL and also wanted to sell it to a hairstyler!
So this is how I did it ad I succeeded:
released the application gpl and told him it's free.
what he payd was for the hairstyles that the application has installed, build only for him and not available for free over the net.
This way everybody wins.
He payd for customizing a software to his needs (a personal version) while the software is available under GPL.

But of course it depends from case to case, what does your software do?

Dude, jkiwi seems pretty cool. Just had a quick peek at the site. My wife will go GAGA over that. Damn thats so much more free time for me. :lolflag:

---

### Post by koenn on 2008-11-27
> **kineem said:**
> yes
Well, then, ... all what is said about selling/making profit of open source still applies, but it applies to that company rahter than to you, and it depends on whether that company will want to go that route ... hard to say. 

I have trouble understanding the following : you are probably a user of open source software. You've experienced the benefits first hand. You would even prefer to use GPL'd libraries for the program you're writing or planning to write. Yet you're planning to deny other people that sort of freedom and benifits by releasing under a restrictive license, in order to please a company didn't create that software, will probably not use it, but just acts as a middleman and pockets the cash. I find that strange. 


I suppose that some sort of dual licensing can solve this for you, as others have pointed out, but you might have to ask an expert about how to do it. Re-licensing GPL'ed sources is not allowed, even if it's your own program, because that means you could revoke a user's right to use your software. Who would risk to use a program if some dude can decide at any time that you're no longer allowed to use it ?
I think that would also be the case for a new version that reuses code from previous versions, versions that are already have been released under GPL. Parts of that code may have been reused in other programs already and it would be hard to tell whether it comes from a gpl'd version 8 or a differently licensed version 9. That company might want users to stop using/distributing code that actually came under a GPL program, or the company might be considered infringing on the GPL for distributing GPL"ed code under a restrivtive license, all sorts of uncertainty everywhere, not good business.

If all versions from the beginning have been released under two licenses, that company can claim that the code they use never was GPL'd to them, so they can license it how they see fit, but it is still kinda muddy to me. 
There are some well-known programs that are (or have been for a long time) dual-licensed. AB's MySQL, I think, although that may have changed since Sun took over.

Anyway, if you also intend to (re-)use existing GPL'ed software, such as libraries, you have no choice. Or actually, you do : don't use them, or release your program under the GPL. 
Some libraries are LGPL and that may be a different case, but if a library is released under the GPL, the programmer is basically telling you : "I wrote this, it's mine and I let you use it, now you do the same. If you don't like that, feel free to use something else."

---

### Post by Ozor Mox on 2008-11-27
> I think that would also be the case for a new version that reuses code from previous versions, versions that are already have been released under GPL. Parts of that code may have been reused in other programs already and it would be hard to tell whether it comes from a gpl'd version 8 or a differently licensed version 9. That company might want users to stop using/distributing code that actually came under a GPL program, or the company might be considered infringing on the GPL for distributing GPL"ed code under a restrivtive license, all sorts of uncertainty everywhere, not good business.

This raises an interesting question. As far as I know, there is no doubt that the author, and therefore copyright owner, of some software can change the licence for a new version of the software. After all, it is their right as copyright holder to do this. But then, are they allowed to use code from previous GPL versions of their software in the new version? Maybe they are the only one allowed to do this, since if other people were using the code in this way they would be infringing on the GPL. How would anyone know what version of the software it came from?

Whenever I think about software licencing stuff, it always makes my head want to explode! :confused:

---

### Post by koenn on 2008-11-27
> **Ozor Mox said:**
> 

Whenever I think about software licencing stuff, it always makes my head want to explode! :confused:
yeah ...
stuff for lawyers, i suppose. 
the workaround is : keep it simple : pick 1 license, stick with it. 
since KISS is also a good idea in programming, that sort of ties together nicely.

---

### Post by kineem on 2008-11-27
> **koenn said:**
>  I have trouble understanding the following : you are probably a user of open source software. You've experienced the benefits first hand. You would even prefer to use GPL'd libraries for the program you're writing or planning to write. Yet you're planning to deny other people that sort of freedom and benifits by releasing under a restrictive license, in order to please a company didn't create that software, will probably not use it, but just acts as a middleman and pockets the cash. I find that strange. 


Thanks for the all replies. Yes I really believe in open source. But I am a student and when it comes to affordance I really have to think twice. I need to sell the  software for now. It is just a matter of affording. If I had enough money I would definitely GPL'd it but because GPL maynt be suitable for companies I searched for a dual licencing or something like that. I had better search the licence types of Apache and Mysql.

---

