---
title: "Conky showing many http and https sites are constantly tracking me"
date: 2016-02-16
forum: Security
---

### Post by ltuser0123 on 2016-02-16
Dear All, 

    I have just installed Conky and I am very pleased with it. However, I notice that the Outbound Connection and Remote Service/Port shows that many http and https sites are tracking me wherever I go online, including when I log on to https banking sites, which is very disconcerting: is this normal?

The one that stands out the most is Facebook, which seems to be based in Ireland. There are also many variants of Akamai and Amazon cloud sites amongst many others; it always varies and they come and go whilst I am online.

I use Firefox, which is set on full security and I always clean all cookies etc before surfing.  I also regularly scan with Clamtk+ fully updated.

Please can you advise.  Many thanks.

---

### Post by matt_symes on 2016-02-16
Hi

> **ltuser0123 said:**
> Dear All, 

    I have just installed Conky and I am very pleased with it. However, I notice that the Outbound Connection and Remote Service/Port shows that many http and https sites are tracking me wherever I go online, including when I log on to https banking sites, which is very disconcerting: is this normal?

I bit of visibility does open ones eyes eh ?

What Firefox browser plugins do you have installed, if any ? 

The are many you can install such as DoNotTrackMe and ublockorigin.

> The one that stands out the most is Facebook, which seems to be based in Ireland.

They're an American company headquartered in Ireland for tax purposes; perfectly legally.

If you're visiting pages with Facebook like buttons, they may be pulled from Facebook.

> There are also many variants of Akamai and Amazon cloud sites amongst many others; it always varies and they come and go whilst I am online.

Akamai and Amazon (in this context) are content delivery networks. They deliver content such as images and video. 

> I use Firefox, which is set on full security and I always clean all cookies etc before surfing.  I also regularly scan with Clamtk+ fully updated.

Most web pages nowadays pull content and scripts from a variety of sources. This is what you're seeing.

Kind regards

---

### Post by Habitual on 2016-02-16
Normal.

---

### Post by coldraven on 2016-02-16
Install the Firefox add-on Ghostery, mine says that it is currently blocking 2078 out of 2080 trackers.
[https://www.ghostery.com/](https://www.ghostery.com/)

---

### Post by ltuser0123 on 2016-02-16
> **matt_symes said:**
> What Firefox browser plugins do you have installed, if any ?

Thanks for all of your replies, especially matt_symes.  I do use blockers, i.e. noscript and ghostery, but I still seem to have a posse of sites following me around.  I don't mind so much on http sites, but it is worrying on https sites like banks.

---

### Post by Habitual on 2016-02-16
Just because you "see" the traffic does not mean you are being "tracked".
How do you expect to get to [https://bank.site.com?](https://bank.site.com?) 

The request has to go out over the wire.

Now, if your browser is closed for over a few minutes and you see traffic to the bank after that, then I'd be suspicious.

---

### Post by matt_symes on 2016-02-16
Hi

> **ltuser0123 said:**
> Thanks for all of your replies, especially matt_symes.  I do use blockers, i.e. noscript and ghostery, but I still seem to have a posse of sites following me around.  I don't mind so much on http sites, but it is worrying on https sites like banks.

Usually it's not that they follow you around, it's more like that's where part of the content you see on your page may be coming from.

You'll find many pages use Google analytics for instance.
 
Is Facebook is following you on a banking site ?

The thing is, privacy went out the window over a decade ago for most people that surf the net. It's just that most people don't realise it until they get visibility.

Remember your DNS requests... and all traffic goes through your ISP... 

Whether this traffic is logged or not is another matter and may hit politics and political will.

Kind regards

---

### Post by mastablasta on 2016-02-17
if you go to facebook and allow facebook.com to no script, then go to bank that uses some of their service (can be as stated a simple like button) then you will see a request from bank site to facebook to provide that like button.

usually online bank site (i mean the site where you do transfers and such) is separated from their "webpage" meant for all customers.

https means only that connection /data transfer that goes from your end to the bank's website is encrypted. if bank uses other outside services on their website they would be contacted from banks side. in other words think of https as tunnel for your data to travel in, so no one can see it. but bank and services connected to them can still see it. e.g. people at the end (bank) and at beginning (you) can still see the data.

also for those that are more worried banks usually have pro option for online banking. which (at least here) usually consist of a special client software, chip for signature (on card or USB) and pin code. no browsers. you can then see how client only connects to bank's servers. and the way transactions is done is that you prepare a request in a packet, encrypt it and send it via encrypted connection to bank for processing. similar process for bank's reply. all logged. it was quite well done, though GUI could be better, and the damn chip with signature worked on windows only.

---

### Post by ltuser0123 on 2016-02-18
Hi,

Of course one accepts that your ISP supplier, with whom you have a legitimate contract has access to your online activity. However, these mysterious sites appearing out of the ether are taking a liberty, but since this appears to be 'normal practise', and since they appear to do no harm, I will just ignore/ block them. However, I take onboard masterblaster's point that some of these external sites are initiated by the banks themselves

Many thanks for all your inputs, much appreciated.

---

