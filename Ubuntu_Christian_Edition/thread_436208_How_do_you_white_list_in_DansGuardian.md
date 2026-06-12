---
title: "How do you white list in DansGuardian?"
date: 2007-05-07
forum: Ubuntu Christian Edition
---

### Post by timzak on 2007-05-07
I like the idea of DansGuardian, but it is blocking aol.com (I have an aol email account and check my email through their web site).  I tried putting "aol.com" in the white list but it still blocks it when I try to go there.  I also tried relaxing the settings back from "strict" and it always blocks aol.com anyway.  How can I whitelist aol.com?

Thanks.

---

### Post by wiseguy on 2007-05-07
If you add aol.com to "Sites Not Filtered", should work.

---

### Post by mfitch on 2008-04-16
also consider greylist
to allow aol mail but still run keyword filtering.

greysitelist

#domains in grey list
#Don't bother with the www. or the http://

#The 'grey' lists override the 'banned' lists.
#The 'exception' lists override the 'banned' lists also.
#The difference is that the 'exception' lists completely switch
#off *all* other filtering for the match.  'grey' lists only
#stop the URL filtering and allow the normal filtering to work.

#An example of grey list use is when in Blanket Block (whitelist)
#mode and you want to allow some sites but still filter as normal
#on their content

#Another example of grey list use is when you ban a site but want
#to allow part of it.

#The greyurllist is for partly unblocking PART of a site
#The greysitelist is for partly unblocking ALL of a site

---

### Post by vmikalinis on 2008-07-25
I'm having a similar issue.  If I add aol.com to the exceptionsitelist.  Aol loads but the formatting is all fouled up.  Obviously dansguardian is ignoring my request to allow the site though unconditionally.  I've seen it happen to other sites also such as yahoo.com......the site loads but all of the images are stripped out because they come from yimg.com....so then that must be added to the exception list.  Is there a way to allow a site and then allow content at that site or do I have to continually go through every site step by step until everything is allowed?  

I'm just trying to filter out dangerous sites such as phishing sites.....I don't want to make the web unusable.  Any help would be appreciated....thanks.

---

### Post by timzak on 2008-07-25
> **vmikalinis said:**
> I'm having a similar issue.  If I add aol.com to the exceptionsitelist.  Aol loads but the formatting is all fouled up.  Obviously dansguardian is ignoring my request to allow the site though unconditionally.  I've seen it happen to other sites also such as yahoo.com......the site loads but all of the images are stripped out because they come from yimg.com....so then that must be added to the exception list.  Is there a way to allow a site and then allow content at that site or do I have to continually go through every site step by step until everything is allowed?  

I'm just trying to filter out dangerous sites such as phishing sites.....I don't want to make the web unusable.  Any help would be appreciated....thanks.

It's been a long time since I posted this.  But since then I have stopped using DansGuardian and started using OpenDNS.  Visit OpenDNS.com for details.  Basically, you just use their DNS settings instead of your ISP's, and they do all the filtering on their end, so there is no slowdown, no configuration, etc.  You do have the option, on their site (after you set up a free account), to check and uncheck certain categories that you'd like blocked or unblocked.  For the most part, I find it a very satisfactory system.

Good luck.

---

### Post by vmikalinis on 2008-07-25
> **timzak said:**
> It's been a long time since I posted this.  But since then I have stopped using DansGuardian and started using OpenDNS.  Visit OpenDNS.com for details.  Basically, you just use their DNS settings instead of your ISP's, and they do all the filtering on their end, so there is no slowdown, no configuration, etc.  You do have the option, on their site (after you set up a free account), to check and uncheck certain categories that you'd like blocked or unblocked.  For the most part, I find it a very satisfactory system.

Good luck.

Thanks, I appreciate your help, but I need to track the pages that users visit and I also noticed that opendns has a very limited number of site exception entries available.  I have to be sure that I can allow all of the sites that I need in the occasion that there is a problem with one.

---

### Post by rahmtech on 2010-11-05
I noticed the last post was in 2008 and here it is 2010.
 
I am using Dansguardian also and have ran into several issues and also with the aol formatting, etc.
 
I sniffed traffic and found out that even though dansguardian allows it through, the information is still modified causing some webpage formats to be garbled such as aol.com.
 
I have also noticed other problems such as connecting to itunes store via itunes, sitebuilder for webpage upload via port 80 and microsoft live xbox account .
 
At this point in time I have not been able to resolve these issues without bypassing dansguarding all together.
 
if anyone has any input, please share.

---

### Post by lilone on 2011-07-12
> I noticed the last post was in 2008 and here it is 2010.

Hi all, I'm not sure about aol.com and I know this is an old thread but if this is useful to someone out here (even though it's now 2011 :P ) - I had this problem using dansguardian and the new yahoo mail. Here are the steps which worked for me:

Add the following two lines to your exceptionsitelist

mail.yahoo.com 
mail.yimg.com

Mails, attachments and the inbox should work and appear as expected now.

Cheers :)

---

### Post by jonnymccullagh on 2011-08-26
Thanks lilone, helped me. j

---

### Post by furikao on 2011-09-20
Thank you Linole!
I love u!

I finally get work the yahoo mail page.

ciao.

---

### Post by Archangelos on 2011-11-16
You don't need to whitelist these sites. You just need to set your filtering strictness up to 160 (young adult). I think it's set on 50 by default, which is probably ok for 5 year olds.

---

### Post by Rakeshvijayan on 2012-02-20
> **lilone said:**
> Hi all, I'm not sure about aol.com and I know this is an old thread but if this is useful to someone out here (even though it's now 2011 :P ) - I had this problem using dansguardian and the new yahoo mail. Here are the steps which worked for me:

Add the following two lines to your exceptionsitelist

mail.yahoo.com 
mail.yimg.com

Mails, attachments and the inbox should work and appear as expected now.

Cheers :) YES Its working

---

### Post by Rakeshvijayan on 2012-02-20
> **Archangelos said:**
>  You just need to set your filtering strictness up to 160 (young adult). I think it's set on 50 by default, which is probably ok for 5 year olds.
 how to do this ..........

---

