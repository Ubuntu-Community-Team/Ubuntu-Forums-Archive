---
title: "How to use Linux legally for business in the US"
date: 2013-02-20
forum: The Cafe
---

### Post by jhargis1012 on 2013-02-20
Hello.

I am doing some research on software patents and how they inhibit businesses in the US from using FOSS.

My question is, basically, what would a business have to do in the US to use Linux in place of Windows/Mac and make sure they are not violating software patents? Violating these patents (for example, including an illegal H.264 codec in a company's system image so that video can be played by employees) present a serious liability to US businesses and could potentially discourage them from abandoning a proprietary OS for a free one.

One portion (of many) of this discussion I do not understand is how does one guarantee their system is clean of illegal codecs? For example, assume if one used his/her package manager to delete any codec-related packages he/she could find. If this person used a web browser to navigate to a website that included in-page H.264 videos or sound effects encoded using MP3, would this content merely not function (meaning, the person would be legally safe but unable to play the content)? Or do web browsers have these illegal codecs built in? I don't understand how website programming works enough to know the answer to this particular question.

I would appreciate any insight on this issue (and/or any thoughts you might have on this subject).

Thank you for your time.

---

### Post by Paqman on 2013-02-20
> **jhargis1012 said:**
> 
One portion (of many) of this discussion I do not understand is how does one guarantee their system is clean of illegal codecs?

By default Ubuntu does not ship with any codecs which might be legally encumbered in some countries. That's why the installer asks you if you want to install codecs when you set up. By default the set of codecs that it does download and install (ubuntu-restricted-addons) are very safe, too.

> 
 For example, assume if one used his/her package manager to delete any codec-related packages he/she could find. If this person used a web browser to navigate to a website that included in-page H.264 videos or sound effects encoded using MP3, would this content merely not function

Correct. No codec, no play. Having said that, browsers are starting to bundle some stuff in. Chrome contains its own implementation of Flash, for example. There's nothing illegal about using a codec bundled within a browser though.

---

### Post by snowpine on 2013-02-20
Some distros ([Fuduntu]("http://fuduntu.org/") comes to mind) have licensed codecs, so you might want to contact the makers of those distros and ask their advice how they did it. :)

---

### Post by Paqman on 2013-02-20
There are completely legal codec packs available for Ubuntu too. Fluendo springs to mind.

---

### Post by jhargis1012 on 2013-02-20
> **Paqman said:**
> By default Ubuntu does not ship with any codecs which might be legally encumbered in some countries. That's why the installer asks you if you want to install codecs when you set up. By default the set of codecs that it does download and install (ubuntu-restricted-addons) are very safe, too.



Correct. No codec, no play. Having said that, browsers are starting to bundle some stuff in. Chrome contains its own implementation of Flash, for example. There's nothing illegal about using a codec bundled within a browser though.

Thank you for that clarification. So it sounds like a business owner would be safe utilizing Ubuntu as a primary system environment (instead of Windows) as long as he or she avoided downloading any problematic codecs.

---

### Post by tgalati4 on 2013-02-20
A bigger risk is using linux to develop a custom enterprise resource planning system (ERP) and as the company grows (an makes money) it's competitors sue the company claiming software patents, effectively shutting it down.  It's a sad state of affairs.

---

### Post by papibe on 2013-02-20
A company may also set up their own repositories.

An example would be to mirror 'Main', and avoid Restricted, Universe, and Multiverse (details about what they are [here]("https://help.ubuntu.com/community/Repositories/Ubuntu")).

Just a thought.
Regards

---

### Post by mastablasta on 2013-02-21
> **jhargis1012 said:**
> Thank you for that clarification. So it sounds like a business owner would be safe utilizing Ubuntu as a primary system environment (instead of Windows) as long as he or she avoided downloading any problematic codecs.
 
often codecs are allowed to be used for free as long as they are not used in a commercial way. i.e. that you would bundle them in the system and then sell them.

---

### Post by kurt18947 on 2013-02-21
I am not an I.P. expert, don't play one on TV and didn't stay at a Holiday Inn.  I would *hope* that a cease and desist letter would be the end of it.  A few factors could enter into it.  One would be if the business were one that 'should have known better'.  For example, a business that deals  with software licensing and I.P.  could be expected to  be aware of such issues.  Mom & Pop's dry cleaning could be excused.  Another, unfortunately in the U.S., is 'how juicy a target is it?'.  It'd be easier to convince a judge or jury that a company sophisticated enough to be very wealthy should be sophisticated enough to know they were using illegal software .... and we want some of their millions.

---

### Post by SeijiSensei on 2013-02-21
Most enforcement at the level of individual businesses happens via the [Business Software Alliance](http://ww2.bsa.org/GlobalHome.aspx).  They do conduct on-site audits of installed software to ensure that there are a sufficient number of licenses purchased for each product.  I doubt they care a whit about Linux in any of its forms.  Mostly they are looking for people running too many copies of Microsoft Office, Photoshop, and AutoCAD.  I also don't think they enforce things like the H.264 patent.  That would be the province of the H.264 rightsholders, the [MPEGLA](http://www.mpegla.com/main/programs/avc/Pages/FAQ.aspx).

---

### Post by jhargis1012 on 2013-02-21
Thank you all for your responses.

> **Paqman said:**
> 
Correct. No codec, no play. Having said that, browsers are starting to bundle some stuff in. Chrome contains its own implementation of Flash, for example. There's nothing illegal about using a codec bundled within a browser though.

If I could revisit this briefly, how do standards such as HTML5 fit in to this? I'm not too familiar with how HTML5 works on a deeper level. If a website designer wanted to add video to a website written in HTML5, is there a special, open format for videos on such a site? OR, would the creator have the option to write the website in HTML5 but use the H.264 format for the video appearing on the site? If the latter, then I assume your original response would apply (that is, "No codec, no play").

---

### Post by pqwoerituytrueiwoq on 2013-02-21
mozilla will not include a h264 codec in there browser (firefox) as it goes against open principals (it also would cost millions in fees)
they will not use the system codec for security reasons (they may have found a fix for that)

google chrome includes a codec, and there own flash player called pepper

[http://en.wikipedia.org/wiki/HTML5_video#Browser_support](http://en.wikipedia.org/wiki/HTML5_video#Browser_support)

---

### Post by SeijiSensei on 2013-02-21
H.264 in the instance you describe is a special case, since a [royalty-free license]("http://www.mpegla.com/main/programs/AVC/Documents/AVC_TermsSummary.pdf") exists for end users to watch many H.264-encoded videos over the Internet:

"In the case of Internet Broadcast AVC Video (AVC Video that is delivered via the Worldwide Internet to an End User for which the End User does not pay remuneration for the right to receive or view, i.e., neither Title-by-Title nor Subscription), there will be no royalty for the life of the License."

As in anything having to do with "intellectual property," there are usually no simple clear-cut rules.  Not installing any of the restricted-extras in Ubuntu seems like the easiest method of ensuring that you are not likely to run afoul of the law.

---

### Post by forrestcupp on 2013-02-21
> **kurt18947 said:**
> I am not an I.P. expert, don't play one on TV and didn't stay at a Holiday Inn.  I would *hope* that a cease and desist letter would be the end of it.  A few factors could enter into it.  One would be if the business were one that 'should have known better'.  For example, a business that deals  with software licensing and I.P.  could be expected to  be aware of such issues.  Mom & Pop's dry cleaning could be excused.  Another, unfortunately in the U.S., is 'how juicy a target is it?'.  It'd be easier to convince a judge or jury that a company sophisticated enough to be very wealthy should be sophisticated enough to know they were using illegal software .... and we want some of their millions.Not necessarily. There were all of those individuals who were sued for downloading mp3s.

> **pqwoerituytrueiwoq said:**
> mozilla will not include a h264 codec in there browser (firefox) as it goes against open principals (it also would cost millions in fees)
they will not use the system codec for security reasons (they may have found a fix for that)

google chrome includes a codec, and there own flash player called pepper

[http://en.wikipedia.org/wiki/HTML5_video#Browser_support](http://en.wikipedia.org/wiki/HTML5_video#Browser_support)And let's clarify that everything Chrome includes is legal. If you install a clean copy of Ubuntu, and don't choose to install the codecs, then install Chrome, you should be legal and have functionality. Note that Chromium does not include these things. You have to install Chrome to get this stuff. Chrome also has a browser based pdf reader included, which Chromium does not.

---

### Post by mamamia88 on 2013-02-21
Just install and use it.  If lawyers are going to come after anyone it would be the distribution maintainers and developers not the people who are actually using it.

---

### Post by kurt18947 on 2013-02-21
> **forrestcupp said:**
> Not necessarily. There were all of those individuals who were sued for downloading mp3s.


Wasn't that more about music piracy, rather than using an unlicensed CODEC?

---

### Post by grahammechanical on 2013-02-21
> I am doing some research on software patents and how they inhibit businesses in the US from using FOSS.

From the research that you have done already just how does a software patent prohibit Free and Open Source Software from being used by a corporate entity?

You seem to be starting from a presumption that FOSS developers are the kind of people that engage in illegal activities. Do you find it incomprehensible that program code can be written without breaching patents or copyright?

It is possible to install Ubuntu using only Free and Open Source Software and we have that option because some people have an ethical reason for not using proprietary code and that reason has nothing to do with it being illegal to use proprietary software.

Have you read about this organization?

[http://www.zdnet.com/blog/open-source/linux-patent-defense-group-expands-open-source-protection/10491]("http://www.zdnet.com/blog/open-source/linux-patent-defense-group-expands-open-source-protection/10491")

I understand that Canonical has signed up to that organization. Sadly, if an inventor/designer does not patent or copyright his work then somebody else will. This has been happening for over 100 years. The inventor is not always the person who gets rich from his invention. It is often the person who sees the business opportunity and takes hold of it.

How a patent/copyright holder uses the power of the patent/copyright is a different matter. Companies like Canonical make money from selling IT services to corporate entities. Have you found one example of a business being taken to court for breach of copyright for having Ubuntu server or desktop installed on the hardware?

Perhaps you would like to share with us the evidence that you have that businesses are actually being taken to court in the US for breach of patent due to using FOSS in their business.

Regards.

---

### Post by SeijiSensei on 2013-02-21
> **grahammechanical said:**
> From the research that you have done already just how does a software patent prohibit Free and Open Source Software from being used by a corporate entity?

You seem to be starting from a presumption that FOSS developers are the kind of people that engage in illegal activities. Do you find it incomprehensible that program code can be written without breaching patents or copyright?

I don't think he believes this at all by my reading.  He is asking whether some versions of some Linux distributions contain software items that are covered by patents in the United States.  The answer to that is yes for distributions that include an H.264 codec or an MP3 codec.  Those issues do not apply to GPL'd and other FOSS software, but those aren't the only things that might be part of a Linux distribution.

Take a look at [Linux Mint]("http://www.linuxmint.com/download.php"), for instance.  They have codec-free versions that are legal to download in the US and Japan where these patents are enforced.  

Also, you mention breach of copyright later in your posting.  That's a very different thing from a patent infringement.  All the software in Ubuntu is copyrighted, with the copyrights held by a wide array of organizations and individuals.  Every download of Ubuntu could constitute an infringement except that agreements like the General Public License explicity grant the end user the privilege to make and distribute copies as long as the rules are followed about derivative works and the required COPYRIGHT notice.

---

### Post by snowpine on 2013-02-21
*cough, cough*

> **snowpine said:**
> Some distros ([Fuduntu]("http://fuduntu.org/") comes to mind) have licensed codecs, so you might want to contact the makers of those distros and ask their advice how they did it. :)

Did you follow my suggestion and contact people who actually know what they are talking about (as opposed to random internet forum weirdos like myself)?

---

### Post by SeijiSensei on 2013-02-21
> **Paqman said:**
> There are completely legal codec packs available for Ubuntu too. Fluendo springs to mind.

Fluendo charges &#8364;28 ($37 US) for their complete package of licenses and codecs.  They used to be available directly from shop.canonical.com, but now you just get an "[out-of-stock]("ubuntuforums.org/newreply.php?do=newreply&p=12521373")" message from there???

After the initial year, Fluendo charges &#8364;7 per year for support, or less on a multi-year contract.  Intriguingly all the documentation refers to these charges as a "support fee" but do not address whether your rights to use the software continue on after the initial year comes to an end.  Still, for a business looking to stay on the right side of the law, these are pretty small prices to pay.  You can limit your costs to just the machines/employees who need these capabilities.

---

### Post by jhargis1012 on 2013-02-21
> **grahammechanical said:**
> From the research that you have done already just how does a software patent prohibit Free and Open Source Software from being used by a corporate entity?

You seem to be starting from a presumption that FOSS developers are the kind of people that engage in illegal activities. Do you find it incomprehensible that program code can be written without breaching patents or copyright?

It is possible to install Ubuntu using only Free and Open Source Software and we have that option because some people have an ethical reason for not using proprietary code and that reason has nothing to do with it being illegal to use proprietary software.

Have you read about this organization?

[http://www.zdnet.com/blog/open-source/linux-patent-defense-group-expands-open-source-protection/10491]("http://www.zdnet.com/blog/open-source/linux-patent-defense-group-expands-open-source-protection/10491")

I understand that Canonical has signed up to that organization. Sadly, if an inventor/designer does not patent or copyright his work then somebody else will. This has been happening for over 100 years. The inventor is not always the person who gets rich from his invention. It is often the person who sees the business opportunity and takes hold of it.

How a patent/copyright holder uses the power of the patent/copyright is a different matter. Companies like Canonical make money from selling IT services to corporate entities. Have you found one example of a business being taken to court for breach of copyright for having Ubuntu server or desktop installed on the hardware?

Perhaps you would like to share with us the evidence that you have that businesses are actually being taken to court in the US for breach of patent due to using FOSS in their business.

Regards.

Thanks for the link to that organization. It sounds great. I'll have to look into that more.

This thread is a good example of what I mean by companies being afraid to use open source software: [http://ask.slashdot.org/story/03/03/14/071255/indemnity-protection-for-linux](http://ask.slashdot.org/story/03/03/14/071255/indemnity-protection-for-linux)

I mean that any open source programmer means to engage in any illegal activities. I think the vast majority of it is well-intentioned (and in many countries, not illegal at all). Sadly, in the use, patent troll companies can lie in wait holding a patent on some obscure piece of software and then sue. Considering how difficult it is (basically impossible) to KNOW that no one holds a patent on a piece of software you are designing and/or using, US patent law makes it risky for developers and businesses running open source software. At least, that is how I understand it, and my understanding could well be incomplete, which is why I am here seeking some knowledge on the topic! :)

---

### Post by SeijiSensei on 2013-02-22
That Slashdot link is from ten years ago when there was lots of FUD being disseminated by the usual suspects like Microsoft about the supposed risks of the General Public License and open source in general.  The [SCO suit]("http://www.groklaw.net/staticpages/index.php?page=20061212211835541") was ongoing as well. Events happen quickly in the IT world.  What businesses might have thought in 2003, in particular the type of large enterprise the Slashdot poster worked for, and what they think today are miles apart. 

If you're writing a paper on this subject, you need to restrict your sources to perhaps the past five years at most, unless you're planning on digging deep into the weeds and examining things like SCO v IBM|Novell.  Also if businesses were as reluctant to invest in Linux today as they were a decade ago, we wouldn't be seeing stories like [this one]("http://www.infoworld.com/t/linux/linux-savvy-it-pros-are-in-high-demand-low-supply-213180").  And, of course, the worries of the higher-ups in the Slashdot poster's company might be assuaged by [this](http://www-03.ibm.com/systems/z/os/linux/).

Any knowledgeable system administrator these days wouldn't have any qualms about the legality of installing Linux-based servers or using them for software development.  They might not want a Linux server if they are managing a Windows environment, but that's a decision based on practicality rather than concerns about intellectual property.  Desktop Linux has more opportunities to be in violation of patent laws because of the codec issue we've discussed already.  

Now I know that at one time proprietary software developers worried about whether the use of GPL'd tools and libraries might require that they open the source to the proprietary product.  I think everyone agrees nowadays that those fears are not warranted, but there may still be some fearful attorneys out there.  They get paid to worry.

---

### Post by buzzingrobot on 2013-02-22
Don't muddy the waters up by equating patents, copyright, and licensing.  They are three very different things.

I can patent a robot.  That says nothing about licensing or copyright.

I might copyright the ronot's source code. That says nothing about a patent or licensing.

I might neither patent or copyright something, but release/market it by licensing it.

Including patented products in another product is perfectly legal as long as you've acquired the legal right to do that, typically via a license.

Microsoft and Apple products include, I suspect, considerably more licensed products than any Linux flavor.

Also very related to all this is indemnification, whereby a vendor provides financial protection to customers in case a third party sues for alleged intellectual property infringement in the products purchased from that vendor.

---

### Post by forrestcupp on 2013-02-23
> **kurt18947 said:**
> Wasn't that more about music piracy, rather than using an unlicensed CODEC?

Yeah, but my point was that they don't always only go after the big corporations that will make them a lot of money. There have been instances where they went after the little, insignificant people just to use them as an example. That could happen with unlicensed codecs just as easily as piracy, if they wanted to.

---

### Post by jhargis1012 on 2013-02-23
> **SeijiSensei said:**
> That Slashdot link is from ten years ago when there was lots of FUD being disseminated by the usual suspects like Microsoft about the supposed risks of the General Public License and open source in general.  The [SCO suit]("http://www.groklaw.net/staticpages/index.php?page=20061212211835541") was ongoing as well. Events happen quickly in the IT world.  What businesses might have thought in 2003, in particular the type of large enterprise the Slashdot poster worked for, and what they think today are miles apart. 

If you're writing a paper on this subject, you need to restrict your sources to perhaps the past five years at most, unless you're planning on digging deep into the weeds and examining things like SCO v IBM|Novell.  Also if businesses were as reluctant to invest in Linux today as they were a decade ago, we wouldn't be seeing stories like [this one]("http://www.infoworld.com/t/linux/linux-savvy-it-pros-are-in-high-demand-low-supply-213180").  And, of course, the worries of the higher-ups in the Slashdot poster's company might be assuaged by [this](http://www-03.ibm.com/systems/z/os/linux/).

Any knowledgeable system administrator these days wouldn't have any qualms about the legality of installing Linux-based servers or using them for software development.  They might not want a Linux server if they are managing a Windows environment, but that's a decision based on practicality rather than concerns about intellectual property.  Desktop Linux has more opportunities to be in violation of patent laws because of the codec issue we've discussed already.  

Now I know that at one time proprietary software developers worried about whether the use of GPL'd tools and libraries might require that they open the source to the proprietary product.  I think everyone agrees nowadays that those fears are not warranted, but there may still be some fearful attorneys out there.  They get paid to worry.

Well said. Thanks for your input.

Edit: although, one could argue that both those links (the Linux job one and the IBM one) are quite possibly referring to corporate - backed distributions such as Red Hat or Ubuntu with Canonical support (in both cases, I'm sure the supporting corporation would protect clients from patent lawsuits should they come along). In writing my original post, I really had in mind a small business maintaining its own implementation of Linux (that is, with no outside support or guarantees).

---

### Post by alexfish on 2013-02-23
> **forrestcupp said:**
> Yeah, but my point was that they don't always only go after the big corporations that will make them a lot of money. There have been instances where they went after the little, insignificant people just to use them as an example. That could happen with unlicensed codecs just as easily as piracy, if they wanted to.

It's amazing how insignificant people have a lot of Significant Power

BEWARE OF INSIGNIFICANT PEOPLE !

BEWARE OF LEGAL :: IT COULD PROVE TO BE ILLEGAL :: BY Insignificant people

Think that somes up from you know where .

---

### Post by TheFu on 2013-02-26
> **jhargis1012 said:**
>  H.264 format for the video appearing on the 

A few years ago the MPEG Group agreed to make h.264 codecs free from any license fees worldwide for playback.  It is only when creating videos that use this codec commercial (selling) that anyone in the world would care.

You seem to be overly concerned about video codecs. In the business  world, video rarely has anything to do with business.  It just never comes up.

Wikipdia covers the license for each popular codec very well. I suggest you review those articles.

For the broader question, my USA-based businesses use Linux on almost all our machines. It runs the servers and some desktops.  We have a BYOD stance for end-users, so whatever machine each worker wants to use is their own business OS licenses are their problem too. None of our people are "underpaid", so they all have a Core i5 or better primary machine ... er ... that came with a Windows7 license. Our servers speak common, open, protocols, so I don't really care what client is used - OSX, Windwos, Linux, Android, or a dumb phone.  If it works, fine.   I manage the security aspects.

Using Linux on servers is much, much easier than using Windows.  If the company uses F/LOSS software to run the business, ZERO license tracking is necessary.  

Our businesses are run using the free versions of:
* Zimbra
* Redmine
* vTiger
* Alfresco
* LibreOffice
I have no worries about licenses for those tools or being sued for copyright or patent infringement.  Since we are a consulting business, our business worth is in our people and their skills, not the software used or some equipment.  We are paid to solve problems in a cost effective manner.  We always consider F/LOSS solutions, but the customer makes the final decision. In the industry that we consult, most of the time, F/LOSS is not available to solve these problems.

We were using VMware ESXi previously. 
License issues caused by VMware made us drop it for KVM. We've been happily running KVM the last few years.

I mentioned that almost all our servers run Linux.  We do have 1 accounting server ... running Quickbooks.  Sometimes it is not worth the fight (or effort) to demand a Linux tool be used.

BTW, Windows8 will not provide video codecs that Win7 did. That will be an add-on license, so everyone will be in the same boat going forward.  OTOH, most desktop users do not need any video codecs at all, so why should it be deployed/purchased?

A few organizations that you might want to read up on:
* FSF
* EFF
* Google
* Facebook
* Twitter
* IBM
* Redhat
* Amazon
* Rackspace {or any hosting provider - hostmoster, bluehost, ... linode, Amazon}
* GoDaddy
* {insert any of 1,000s of ISPs}

Seems that many, many, many businesses are not having too many problems using Linux at all.

---

