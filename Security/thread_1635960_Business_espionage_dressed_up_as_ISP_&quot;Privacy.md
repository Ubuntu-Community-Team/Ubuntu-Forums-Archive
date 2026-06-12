---
title: "Business espionage dressed up as ISP &quot;Privacy&quot; policies?"
date: 2010-12-02
forum: Security
---

### Post by Hadeda on 2010-12-02
A US ISP's "privacy" policy basically states that they will collect any and all of your data (email, posts, surfing etc ) and then "share" it".

Question(s):

Can someone please direct me to a "checklist" which can suggest counter measures for **non-geeks**? 

How can we function if we cant trust our ISP?

Are there some specific 'tricks' in Ubutu to foil rogue ISPs? 

If yes, it would be a great 'selling point', especially for professionals concerned that rogue ISPs could "share" their intellectual property.
This could be a huge issue for telecommuters too.

Thanks!

---

### Post by Trougedoor122 on 2010-12-02
What ISP is this? Do they indicate who they are "sharing" it with?

You could always make sure your important stuff is encrypted with SSL. Then maybe switch ISP's?

---

### Post by stlsaint on 2010-12-02
This is not a ubuntu specific issue you are referencing here. This involves network transmittal. If you are worried of such things than you need to use a internet proxy like TOR or encrypt your data with a VPN!

---

### Post by CharlesA on 2010-12-02
What ISP is it?

---

### Post by pricetech on 2010-12-02
I too would like to know what ISP and can you point us to the document from which you got this ??

---

### Post by bodhi.zazen on 2010-12-02
> **Hadeda said:**
> A US ISP's "privacy" policy basically states that they will collect any and all of your data (email, posts, surfing etc ) and then "share" it".

Question(s):

Can someone please direct me to a "checklist" which can suggest counter measures for **non-geeks**? 

How can we function if we cant trust our ISP?

Are there some specific 'tricks' in Ubutu to foil rogue ISPs? 

If yes, it would be a great 'selling point', especially for professionals concerned that rogue ISPs could "share" their intellectual property.
This could be a huge issue for telecommuters too.

Thanks!

I would consider all activity on "the internet" to be public domain and expect such behavior.

You can increase your privacy with encryption (https , ssh, VPN), the use of a proxy, and TOR. Be careful with cookies, check out flash cookies, and use NoScript.

I do not believe there is any such thing as total and complete privacy over the internet, especially where your IP provider is concerned.

If you do not find the terms of your IP provider acceptable, find another.

---

### Post by OpSecShellshock on 2010-12-03
A lot of these policies are kind of self-protective on the part of ISPs as well. It's not necessarily that they gather/use the information currently, or that they ever have in the past, but that if they ever do they want to be able to say they told you they might.

---

### Post by SeijiSensei on 2010-12-03
Then there are abominations like [Phorm](http://yro.slashdot.org/article.pl?sid=08/11/22/0221226&tid=158).

If you can't switch ISPs, considering obtaining a virtual server from someone like linode.com.  Then you could set up an OpenVPN tunnel to the server and push all your outbound traffic through the encrypted tunnel.

---

### Post by Ahava591 on 2010-12-07
> **Hadeda said:**
> A US ISP's "privacy" policy basically states that they will collect any and all of your data (email, posts, surfing etc ) and then "share" it".
...
Can someone please direct me to a "checklist" which can suggest counter measures for **non-geeks**? 
...
How can we function if we cant trust our ISP?
...
Are there some specific 'tricks' in Ubutu to foil rogue ISPs? 
....

I have removed some of your OP from my quote-reply, only to save space; it is not because I consider what I removed to be irrelevant. 

Does the ISP policy in question actually state that they are inevitably going to "share," your information? The way you explained it, they have actually put down in writing that they are going to collect everything and that they are going to share it.

Anyway, the problem, if you choose to see it as one, is with things like CALEA. If I remember correctly, it requires all telecommunications providers in the U.S. to use hardware and software which allows law enforcement agencies to monitor all telephone and, (as of 2005/2006,) network communications taking place within the U.S. 

So I don't think the characterization of "rogue," ISP's as such is right. They're obeying the law, for better or for worse, not acting of their own accord.

I am sorry I don't have any specific help for you; I am (obviously,) not a security person. I suggest reading the stickied security thread(s) though.

Good luck.

---

### Post by Boondoklife on 2010-12-07
+1 for VPN, really it is the only way that I could see of completely bypassing your ISP's right to snoop.  You would also have to make sure all traffic is routed through the VPN and not just through your ISP.

**BUT**,
unless you use a trusted out of country VPN, your traffic could just be listened to on their end by their ISP. You would also need to read their T&C's to make sure that they can not be bullied by any particular governing body into giving up their logs and what not. 

Then again there is always the fact that you will have to pay for high quality VPN service and unless you have some anonymous way to get them money, the idea is short lived as you would leave a paper trail right to their door.

---

### Post by Hadeda on 2010-12-15
Thanks for giving such invaluable feedback. I apologize for my delayed response.    

This is not a post seeking to fix a specific Ubuntu technical issue. It is to see if Ubuntu has reliable tools for professionals to communicate their highly valuable and sensitive intellectual property to clients (and vice versa).    

Professional law-enforcement can collect information after having obtained a court order.  [https://www.eff.org/deeplinks/2010/12/breaking-news-eff-victory-appeals-court-holds](https://www.eff.org/deeplinks/2010/12/breaking-news-eff-victory-appeals-court-holds)   But the emphasis is on 'professional' as in having sworn an oath that the information gathered will not be peddled to competitors and if it is, there will be severe consequences!  

Having a for-profit ISP store and “share” info could result in a motive for them to collect more revenue through peddling copied intellectual property than giving us reliable service.    

Protecting and communicating valuable intellectual property is a technical issue. Can the Ubuntu gurus (or others) help us all to find ways to remove the means and opportunity for others to peddle our data? Ubuntu would then be miles ahead of other platforms.    

THANKS!!!    

P.s.: One can change ISP's, but that is not the point.

---

### Post by Boondoklife on 2010-12-15
The issue you are looking to face is just a matter of how the internet works; it communicates in plain text, unless you are on an encrypted line (SSL, VPN, etc). The only real way to FIX the issue is not a change in the os but a change in how sites are hosted and servers connect.

A very simplified solution would be to have encrypted connection options to every site and server. This would have to be put into place on the servers side. An example is you can browse some sites in SSL, it atleast blocks your ISP from reading what you are reading and seeing what you submit. But this idea would also call for all servers (mail, chat, news, ftp, etc) to move to encrypted communication.

Now another thing to think of is even this would not save you as if you are visiting a "Ristricted/Censored" site, you are still going to communicate on an IP level. Now any ISP is going to have logs of your traffic, and if they know the offending IP it is just a matter of seeing who went to it. This is how they catch people going to sites they should not be, even if the traffic is encrypted.

Now the only way to fix that would be to have some sort of a random addressing system, but this would not work as your IP is like your internet home address. Imagine the mailman trying to deliver mail to a street full of homes with addresses that constantly change... See the delema.

The only Faux solution would be to route ALL of your traffic over a VPN but this still has flaws as they must answer to someone too. Hope that clears it up some for ya.

EDIT:
On a further note, if you are just looking for a way to communicate with your home office  then setup a VPN server that your road-warriors can connect to and have  all your traffic go through it. This will make sure you have control  over whom they can communicate with and at what level. Just keep in mind, if they are able to browse the internet through the VPN connection then your company's ISP will have access to any unencrypted data that leaves your network or is coming in to it. This is where good security policies come in and a competent admin.

---

### Post by bodhi.zazen on 2010-12-15
> **Hadeda said:**
> Thanks for giving such invaluable feedback. I apologize for my delayed response.    

This is not a post seeking to fix a specific Ubuntu technical issue. It is to see if Ubuntu has reliable tools for professionals to communicate their highly valuable and sensitive intellectual property to clients (and vice versa).    

Professional law-enforcement can collect information after having obtained a court order.  [https://www.eff.org/deeplinks/2010/12/breaking-news-eff-victory-appeals-court-holds](https://www.eff.org/deeplinks/2010/12/breaking-news-eff-victory-appeals-court-holds)   But the emphasis is on 'professional' as in having sworn an oath that the information gathered will not be peddled to competitors and if it is, there will be severe consequences!  

Having a for-profit ISP store and “share” info could result in a motive for them to collect more revenue through peddling copied intellectual property than giving us reliable service.    

Protecting and communicating valuable intellectual property is a technical issue. Can the Ubuntu gurus (or others) help us all to find ways to remove the means and opportunity for others to peddle our data? Ubuntu would then be miles ahead of other platforms.    

THANKS!!!    

P.s.: One can change ISP's, but that is not the point.

Encrypt the message.

---

### Post by Hadeda on 2010-12-21
Thanks again for clearing this up for me - I get the picture.

Perhaps there is one last question. 

Does anyone know of a structured Ubuntu security course addressing above issues targeted at lay folks such lawyers or accountants?

---

### Post by Boondoklife on 2010-12-21
You don't need an Ubuntu centric class for this, if you check I'm sure one of the local colleges would have internet security classes available. The internet is an abstract idea which has a certain core functionality and flaws, ALL OSs are victim to them.

If you go the route [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") suggested, make sure that you use a strong password to encrypt the message.

---

### Post by Hadeda on 2010-12-23
Excellent advice, thank you!

---

