---
title: "Should I reply to a vendor that won't release source?"
date: 2008-12-13
forum: The Cafe
---

### Post by steviefordi on 2008-12-13
I recently purchased a 'Leapfrog tag reading system' for my nephew for christmas. It's basically a pen like device that you download books onto, then as you drag the pen accross the page of the book it reads for the child. This device comes with software for loading the pen with different books, however, the software is only for Windows and Mac OSX (don't you just love the big corporates assumption that everyone uses one of these OSes!).

I emailed their support department to ask if there was a linux version of the software - to which they said no. Then I asked for the source code, thinking I could either get it working, or work out what it was doing. Again they said no, they don't release the source.

Now I feel suspicious, like there must be something to hide. I mean why would I want to run software on my PC that the writers are not prepared to be open about? It could be doing anything to my machine. Of course they might be worried I'm going to try and profit from their software, but I'm not. In fact I would return a *nix version of the source back to them if I could get it going.

Question is, do I reply to their email saying I can't have the source, telling them that closing it off makes me extremely suspiscious? Or do I just say to myself "that's life!", they're not going to change their minds, and forget about it?

---

### Post by Paqman on 2008-12-13
Only open source projects release their code. You're never going to get it out of them, no matter how many emails you write.

---

### Post by dannytatom on 2008-12-13
> **steviefordi said:**
> just say to myself "that's life!", they're not going to change their minds, and forget about it?

You're better off goin' with the flow, it's highly (highly) doubtful you'll change their minds.

---

### Post by pp. on 2008-12-13
> **steviefordi said:**
> Or do I just say to myself "that's life!", they're not going to change their minds, and forget about it?

Either that, or:
[LIST]
[*]try and run the software in Wine
[*]send the device back stating that when buying you weren't made aware of the fact that it worked only in conjunction with a particular proprietary product which not everyone happens to own.
[/LIST]

Depending on where you live, you might be entitled to reverse engineer the software in order to interface it to your existing system(s). If you care to do so.

> **Paqman said:**
> Only open source projects release their code.

That is not true.

---

### Post by Eisenwinter on 2008-12-13
> **pp. said:**
> 
"Only open source projects release their code"
That is not true.
Technically, it is. Since the source is released, the source is open to the public (**open** source).

I think your argument here is whether they are officially treated as open source projects, though.

---

### Post by mr.propre on 2008-12-13
> **Eisenwinter said:**
> Technically, it is. Since the source is released, the source is open to the public (**open** source).

I think your argument here is whether they are officially treated as open source projects, though.

True, but what allot of people are mistaking at is that opensource = free as in free beer. Atleast in Belgium, because the word free means most of the time gratis.

@ topic: I agree with dannytatom, go with the flow. You can't expect people (or a company) to give you the source code, that's not what you paid for, you just paid for the software. You could say that it's unfair because it doesn't work on Linux, but when you bought the pen you probably knew the minimum requirements. You cant expect to work on Linux when it doesn't say Linux.

---

### Post by Eisenwinter on 2008-12-13
I'd say he can VM windows and use it there, or use it under wine.

Or of course... return the product, and get something else, see if you can swap it for something.

---

### Post by Eclipse. on 2008-12-13
You are never going to get a proprietary company to release their source code by asking them in a email and if I'm going to be perfectly honest why should they.

Sorry but your best chance is wine.

---

### Post by Swagman on 2008-12-13
By emailing them his wish to be able to run their program on Linux he has done the best he can do.
They are now aware there is a demand for a linux port. If only people would do this for all programs instead of quietly just trying to get it going under emulation.

Personally, I can't see the point in companies not making available the source code to their hardware drivers.

It's the hardware they are trying to sell, their drivers are included free for windows/mac. So by not... at the very least making the source available, they are alienating a market.

---

### Post by sub2007 on 2008-12-13
> **steviefordi said:**
> however, the software is only for Windows and Mac OSX (don't you just love the big corporates assumption that everyone uses one of these OSes!).

Because over 99% of desktop users do? If you were allocating resources would you allocate developer time to developing for a system that less than 1% of people use? We know full well that's the situation when we install Linux to our systems. We can't expect them to put their money into coding that and we certainly can't go asking them for their source code. They'd probably be worried that you were a rival product looking to see how their driver works or modify if for your own project, as that's all it's useful for really. Unless you are a hardcore developer you couldn't make a Linux version out of just the source code as it would be a matter of porting all the driver handling to a Linux system - it wouldn't be just a matter of ./configure, make, make install.

As mentioned, your best option is to run an instance of Windows (VM or dual boot). Wine in my opinion would be useless as Wine has no driver handling.

---

### Post by Bölvaður on 2008-12-13
if you are confident that you could port this program to linux you should convince them to hire you for that job for the price of the device.
That way we get more linux programs, they get cheap solution, and everyone is happy.

---

### Post by daynah on 2008-12-13
When you create a program, you do have every right to keep the code to yourself. Similarly, we may desperately want the recipe to the cheese dip from Moes, but they have every right to keep that recipe to themselves. They do this because they don't want other people using their own recipe/code against them on the market.

Obviously, I think there are other ways to view this situation if I'm here, but their though process isn't completely ridiculous by any means.

---

### Post by steviefordi on 2008-12-15
Ok, after much thought I think I'm going to leave it. There was just something in my head nagging me to make a point to the company in question. I know I put myself into a minority when I chose my OS, and I also knew the requirements needed when I purchased the product.

However, as the product is for my nephew and his household uses Windows, it's not really a problem for me. I do like the products this company sells and would like to buy them for my daughter. Perhaps when I do I will try harder to get the more info out of the company to write the drivers and software myself.

even as suggested :
> f you are confident that you could port this program to linux you should convince them to hire you for that job for the price of the device.
That way we get more linux programs, they get cheap solution, and everyone is happy.

---

### Post by timzak on 2008-12-15
> **steviefordi said:**
> I recently purchased a 'Leapfrog tag reading system' for my nephew for christmas. It's basically a pen like device that you download books onto, then as you drag the pen accross the page of the book it reads for the child. This device comes with software for loading the pen with different books, however, the software is only for Windows and Mac OSX (don't you just love the big corporates assumption that everyone uses one of these OSes!).

I emailed their support department to ask if there was a linux version of the software - to which they said no. Then I asked for the source code, thinking I could either get it working, or work out what it was doing. Again they said no, they don't release the source.

Now I feel suspicious, like there must be something to hide. I mean why would I want to run software on my PC that the writers are not prepared to be open about? It could be doing anything to my machine. Of course they might be worried I'm going to try and profit from their software, but I'm not. In fact I would return a *nix version of the source back to them if I could get it going.

Question is, do I reply to their email saying I can't have the source, telling them that closing it off makes me extremely suspiscious? Or do I just say to myself "that's life!", they're not going to change their minds, and forget about it?

Hi,

A little off-topic from your post, but I've actually been looking into this system, but our household is also moving away from proprietary operating systems.  Is there no way to make the tag system work in linux?  In other words, does it require propietary software, or can you load the software via web interface and usb port?

Second question:  If it will not work in Linux period, how often does it need to access a Windows computer?  I have an XP machine at work, so I can do this, but depending on how often one must connect the tag to a computer, it might not be worth my while.  Can you load multiple books into the pen, or only one at a time?

Thanks, I hope you can help me out.

Regards.

---

### Post by linuxguymarshall on 2008-12-15
The weaknesses of proprietary. Why wont Microsoft release their source, why wont Apple release theirs (I could use final cut on linux for free). Its business and it makes them money. Look into open source alternatives. Like a Linux PDA 
(A tad bit expensive)  or something else.

---

### Post by Blutack on 2008-12-15
@linuxguymarshall You can use final cut on linux for free?  How/what/when/where?  Why have I been using Cinelerre all this time!?
@O.P Is it really worth it?  Virtualbox (the proper version from Sun w/USB) and XP handles this type of thing great for me.  If it really bothers you, send an email to the FSF and they'll hassle Leapfrog for you.

---

### Post by steviefordi on 2008-12-16
timzak:
As far as I know there is no way of getting this to work on a linux system. I did read a post somewhere that said it sort-of works with wine, but I haven't tried it myself.

As for how often you need to connect the pen to your PC, well that's up to you. I think the tag reading pen can hold four books worth of data. It also somehow, (not sure how) monitors your childs reading progress and will report on this when connected. So if your child gets through lots of books, and you're the sort of parent that wants to montior your childs progress regularly, then you will be connecting the device to the PC often.

On top of that, you could always contact them and help increase the pressure to bring out a linux version. If enough of their (potential) customers show a requirement for a linux version, then I'm sure they'd be more forthcoming in producing one.

Hope this helps
Cheers
Setve.

---

### Post by PartisanEntity on 2008-12-16
I would have to side with what most people have said here. If the application is proprietary then they have the right to refuse to send you any source code.

Unfortunately there is not much more that can be done.

---

### Post by taqkavar on 2008-12-16
In addition to what people above me have said, I'd like to pint out that the whole concept of copyleft, the GPL license which linux uses kinda started in a very similar manner: A product needed modification ( in your case its linux compatibility ) and the vendor refused to release the source code for that product, and refused to improve the product itself.
So in a sense you just rediscovered this whole dispute.

---

### Post by timzak on 2008-12-16
> **steviefordi said:**
> timzak:
As far as I know there is no way of getting this to work on a linux system. I did read a post somewhere that said it sort-of works with wine, but I haven't tried it myself.

As for how often you need to connect the pen to your PC, well that's up to you. I think the tag reading pen can hold four books worth of data. It also somehow, (not sure how) monitors your childs reading progress and will report on this when connected. So if your child gets through lots of books, and you're the sort of parent that wants to montior your childs progress regularly, then you will be connecting the device to the PC often.

On top of that, you could always contact them and help increase the pressure to bring out a linux version. If enough of their (potential) customers show a requirement for a linux version, then I'm sure they'd be more forthcoming in producing one.

Hope this helps
Cheers
Setve.

Thanks, Steve.

I'm left with the unsettling decision of making this pen work with 5 books or less (load it up once at work, and never again), take the pen to work with me every time I want to load more books or check my son's progress, or upgrade my wife's computer to XP instead of Ubuntu, like I've been planning on.  She's currently using Win2k and the software won't load on that OS either.

Big bummer.  Taking the pen back is not an option for my wife.  She's really set on our son using this thing and from what I've read, it really seems like a great thing for him.  On the one hand, having one current Windows machine in the household isn't such a bad thing, on the other hand, having to spend money on an OS is not something I am looking forward to.  Just so no one suggests, I am not open to any illegal acquisition of software, so if I get XP, it will be a legal purchase.

Thanks again for your clarification, Steve.

Tim

---

### Post by oedipuss on 2008-12-16
Don't forget to try a virtual machine.
Most are pretty easy to use by now, like virtualbox. Chances are it will work, and will save you the time of dual booting. Just check if it supports USB (binary non-free virtualbox does, I don't know about vmware etc)

I'm not sure of the legal status though.. I think it's against the EULA on some windows editions, but I suppose that's not a big issue. It can't be considered piracy by any strech of imagination if you're using a valid license.

---

