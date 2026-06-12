---
title: "Do not buy anything from Foxconn!"
date: 2008-07-23
forum: The Cafe
---

### Post by TheAlmightyCthulhu on 2008-07-23
I've been emailing them and blogging about a horrid experience with their G33M-S motherboard not supporting ACPI correctly at all:

The latest email they shot me was,

Dear Ryan:

This board was never certified for Linux.  It is only certified for Vista.  See URL below.  So please test under Vista.  Does this issue also occured under Vista or Winxp?

[http://www.foxconnchannel.com/product/Motherboards/certification.aspx](http://www.foxconnchannel.com/product/Motherboards/certification.aspx)

My reply:

Well, this is a replacement for a dead Intel board (a 945g that fully supported ACPI), Vista was never really up for consideration, and I’m not about to go buy a copy to find out.

The ACPI specs are there for a reason, and broken BIOS’s like what is in this motherboard are the reason standard ACPI does not work,I've taken the liberty of filing the report in Red Hat's Bugzilla tracking system, and posting the contents of my kernel error log on my blog, as well as complained loudly on Newegg, so hopefully this will save other people from a bad purchase, and hopefully kernel.org can work around your broken BIOS in 2.6.26, as I understand that kernel is more forgiving of bad motherboards built for Windows.

You guys are only hurting yourselves in the long run, by using bad BIOS ROMs, as people like me are quite vocal when dealing with a bad product.

---

### Post by LaRoza on 2008-07-23
They have a point, it wasn't built for Linux ;)

---

### Post by TheAlmightyCthulhu on 2008-07-23
> **LaRoza said:**
> They have a point, it wasn't built for Linux ;)

I've been dissecting it and trying to find out what the hell it's doing, when I go to reassemble it, I get so many errors and warnings that it's really scary that even Windows could support something this heinously busted.

If you're wondering, it's an American Megatrends BIOS.

LaRoza: When was the last time you saw a commodity motherboard that proudly proclaimed "Built for Linux"? :P

---

### Post by LaRoza on 2008-07-23
> **TheAlmightyCthulhu said:**
> 
LaRoza: When was the last time you saw a commodity motherboard that proudly proclaimed "Built for Linux"? :P

[http://www.asus.com/products.aspx?l1=3&l2=11&l3=572&l4=0&model=1872&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=11&l3=572&l4=0&model=1872&modelmenu=1)

That is the issue, the hardware doesn't support it and Linux comes without any guarantees.

---

### Post by TheAlmightyCthulhu on 2008-07-23
It works famously til I try to suspend or hibernate, then all kinds of hell.

Know of any good quirks to try?

BTW offtopic, who do you think would win in a fight, me or Borg Queen? :lolflag:

---

### Post by TheAlmightyCthulhu on 2008-07-24
[B]Dear Ryan,

Making idle treats is not going to solve anything.

As already stated this model has not been certified under Linux nor supported.

As you are unhappy with the product- using a non-support operating system nor certified, please contact your reseller for a refund.[/B]

And me:

[B]Yeah, well, I allege that you guys thoroughly suck.

Learn how to write a BIOS before you go selling hardware with falsified specs.[/B]

---

### Post by Joeb454 on 2008-07-24
I wouldn't be at all surprised if you got exactly the same response again.

Then again, I wouldn't have wasted my time writing that reply

---

### Post by TwiceOver on 2008-07-24
I agree... Don't buy anything from Foxconn.  But for an entirely different reason.

---

### Post by Canis familiaris on 2008-07-24
> **LaRoza said:**
> [http://www.asus.com/products.aspx?l1=3&l2=11&l3=572&l4=0&model=1872&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=11&l3=572&l4=0&model=1872&modelmenu=1)

That is the issue, the hardware doesn't support it and Linux comes without any guarantees.

Luckily I brought an ASUS M2A-VM rather than a Foxconn . :D

---

### Post by arsenic23 on 2008-07-24
When talking to Foxcon you should have tried to be a little less hostile.

I would have said something like,

"I noticed the board I bought is somehow deviating from the ACPI standards.  It would help me out if you could provide me with information about this."

The idea being never mentioning your exact problem ( running the board with linux ) and attempting to get more and more knowlegable people on the phone.  If you can get transfered out of the call center and into the actual company you'd be amazed who you can get ahold of.  The trick is anticipating the various things that they can use to make the problem your fault and making sure the conversation never hits those talking points.

Once you get someone who is actually in the company and not on the suport lines you can get into your problem a little more and make sure they know that you expect them to fix it.  If you call and ask them if they'll fix your problem or complain you'll more then likely get ignored.  You need to sound 100% comfident in the fact that they are going to do you right at the end of the day.  I've gotten companies to do all kinds of odd things that go against their support policies using this method.

As an example, once I had a problem with an exensive magazine subscription constanly arriving in my mailbox ripped in two.  So I called the company up to get my magazine placed into a plastic sleave before shipping.  After about 5 hours on the phone I'd somehow been given the private number for the American distribution manager.  To avoid talking to me and to get the name of the person that gave me her number, I was given a back copy of every issue I'd received in the last year and 3 years of free magazines after that, which always came in a plastic sleave.

---

### Post by TheAlmightyCthulhu on 2008-07-24
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338)

Bad ACPI support on Foxconn G33M/G33M-S motherboards with AMI BIOS

---

### Post by TheAlmightyCthulhu on 2008-07-24
[B]I've been debugging your AMI BIOS, and the ACPI support on it is far from within compliance with the standards, I've dumped out the debugging data into  Canonical's Launchpad bug tracking system so that we may be able to use some sort of a workaround for the bad ACPI tables in your BIOS, I would hope that you will be part of the solution instead of the problem, alienating customers and telling them to go buy a copy of Windows Vista is not service, your product claims to be ACPI compliant and is not, therefore you are falsely advertising it with features it isn't capable of.

I would ask that you issue an update that doesn't make it dependent upon Windows Hardware Error Architecture, but that decision is up to you.

Please find all relevant data here:

Bug #251338 in Ubuntu: “Bad ACPI support on Foxconn G33M/G33M-S motherboards with AMI BIOS”
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338)

I appreciate your consideration in this matter.[/B]

How's this sounding?

---

### Post by arsenic23 on 2008-07-24
> **TheAlmightyCthulhu said:**
> How's this sounding?

Looks good to me, but who are you sending it too ?
If you send it to support it's not going to do any good, also an actual letter would more then likely be better then an email.

I'd send a hard copy to :
> Foxconn
458 E. Lambert Road Fullerton
CA 92835 U.S.A

As well as:
> Foxconn
No.8, JiaXing Road,Yantai Economic & Technological Development
Area,Yantai,Shandong,China
264006

You may also want to send out three copies of each, with different 'att:' at the top.  I'd use:
ATTN: Managment
ATTN: Technician
ATTN: Legal Department

---

### Post by wrtpeeps on 2008-07-24
If its certified for vista, it's certified for vista.

Be like you putting petrol in your diesel car and then moaning cause it doesn't work. :lolflag:

---

### Post by mr.propre on 2008-07-24
> **wrtpeeps said:**
> If its certified for vista, it's certified for vista.

Be like you putting petrol in your diesel car and then moaning cause it doesn't work. :lolflag:

I disagree, if you making the comparison between cars and computers, you can say that a 32 OS wont work on a 64 bit CPU because they both have different 'motors', same as with diesel and petrol engines.

But when you are driving an Diesel, you can expect that you can use the diesel of every thank station and not just of shell (for example). And that's the same with computers, if you have a 32 bit system, you could expect that all 32 bit systems work on it.

But it's a little harder in Motherboard land and it's almost impossible to make it compatible with every OS out there, so they pick one that holds 94% of the desktop computers. Than you have 4% Apple and 2% Linux...

But in the end I don't think that linux doesn't work? Its the ACPI that doesn't work, a feature developed by ... Microsoft.

---

### Post by TheAlmightyCthulhu on 2008-07-24
See my other post, Foxconn is doing this deliberately, they divert Linux to a broke DSDT table.

---

