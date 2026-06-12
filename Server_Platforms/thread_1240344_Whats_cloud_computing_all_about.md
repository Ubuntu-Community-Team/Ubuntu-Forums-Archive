---
title: "Whats cloud computing all about?"
date: 2009-08-14
forum: Server Platforms
---

### Post by hockey97 on 2009-08-14
Hi, I just saw the latest ubuntu version server edition and it says it uses cloud computing. 

I read about it and I think I am still lost as to what it is. 

To my understanding I think it means to use other servers resources like cpu,gpu while your using your own resources at the same time. I  have a feeling that what I think is wrong and can't fully understand what cloud computing is all about.Could someone explain it to me in simple terms?

---

### Post by jocampo on 2009-08-14
In a short and easy words, is like "leasing" internet resources to make your applications scalable. Is a new concept and nice in theory, 'cause you'll use what you need and nothing more but allow you to expand.

[http://en.wikipedia.org/wiki/Cloud_computing]("http://en.wikipedia.org/wiki/Cloud_computing")

HP has a similar concept in terms of hardware with a server called Super Dome. It has several CPUs, lot of RAM, etc, but they install the whole stuff. The company just starts using what they need but if in a future (months, years, etc) needs more, the additional CPU, RAM, whatever...is activated remotely .... allowing to application to expand over the time dynamically.

---

### Post by scorp123 on 2009-08-14
> **jocampo said:**
> Super Doom.  Super **_Dome_** .... :D

> **jocampo said:**
>  It has several CPUs, lot of RAM, etc, but they install the whole stuff. The company just starts using what they need but if in a future (months, years, etc) needs more, the additional CPU, RAM, whatever...is activated remotely .... allowing to application to expand over the time dynamically. Still ... the price range of that thing (somewhere in the millions $$$ ...) will make sure that only really big companies will even think of looking at the thing :D

And you better run Linux on it ... because let's face it: The other OS options suck. Windows on such a machine? Bleeeeaaagh. What a waste. And HP-UX? OK, if you have no other choice. But HP-UX as a Unix is really really "ugly" and looks and feels veeeeery outdated.

But to get back to the topic:

One nice and practical example of "cloud computing" is leasing/buying storage. Let's suppose you're a start-up and you'd like some form of "remote backup" to keep your data safe. Sure: You could buy one additional building, buy tons of storage servers, get a leased-line to that server room there .... But that's going to cost you.

Enter cloud computing: There are services such as "Amazon S3" and many other vendors that allow you to buy storage space. So instead of being forced to roll your own storage infrastructure you'd instead buy or lease as much storage you want or need .... And as your business and your storage needs grow you could easily buy more storage space.

[http://aws.amazon.com/s3/](http://aws.amazon.com/s3/)


Another example of "cloud computing" is to buy or lease servers remotely.


So let's assume again that you're a startup and that your hardware budget is quite limited. Let's suppose that for a single project you all of a sudden need more computational firepower. Lots more. What are you going to do? Rent the hardware and have it shipped to you? Sure. Except that this will cost so much that you might as well buy it right away. Or sweet-talk to vendors such as SUN Microsystems and make use of their "60 days free trial" for their servers? Sure. Too bad if the project takes a bit longer. And what if those servers somehow get damaged? Are you sure your insurance will cover that? Too risky.

Enter cloud computing again: You buy or lease as much computational firepower as you temporarily need. No shipping and handling costs, no hardware that you need to return after 60 days ... it's just there when you need it. Or gone when you don't need it anymore.

[http://aws.amazon.com/ec2/](http://aws.amazon.com/ec2/)


(NO, I don't work for Amazon ... But their web site was on top in my Google search :D  )

---

### Post by jocampo on 2009-08-14
> **scorp123 said:**
> Super **_Dome_** .... :D

Sorry, typo... was writing fast and english is my second... ;-)

> 
 Still ... the price range of that thing (somewhere in the millions $$$ ...) will make sure that only really big companies will even think of looking at the thing :D

Right, I know that... and no one said is cheap, is powerful hardware for big companies who can afford it; was using it as an scalability example.

> 
And you better run Linux on it ... because let's face it: The other OS options suck. Windows on such a machine? Bleeeeaaagh. What a waste. And HP-UX? OK, if you have no other choice. But HP-UX as a Unix is really really "ugly" and looks and feels veeeeery outdated.

Right about Windows, but I've seen Data Center on it (a famous bank which I won't mention) and runs really good. Not sure about your comment that HP-UX is "ugly" and outdated, not enough facts from my side to discuss that. 

Anyway, was trying to use Super Dome as an parallel for cloud ...

---

### Post by Dr Small on 2009-08-15
> **scorp123 said:**
> (NO, I don't work for Amazon ... But their web site was on top in my Google search :D  )
How can we be sure? ;) That was a nice sales pitch, by the way :)

---

### Post by scorp123 on 2009-08-15
> **jocampo said:**
> Not sure about your comment that HP-UX is "ugly" and outdated, not enough facts from my side to discuss that.  I worked for Hewlett-Packard 2000 until 2007. So yes, I know HP-UX. But since 2007 I work for a SUN partner and now I get to work a lot with Solaris 10 and OpenSolaris. The differences are ***WOW*** ... Solaris is super-sexy compared to HP-UX. (But Linux is of course the sexiest of them all ... )

If OS were vehicles than HP-UX would be an ugly 40-ton truck. It works, it delivers, it can take huge payloads, but it's ugly and you need to know what you do to drive this thing. Solaris would then be the "Millenium Falcon" from Star Wars .... :lolflag:

---

### Post by scorp123 on 2009-08-15
> **Dr Small said:**
>  How can we be sure? ;) I suppose they bribed Google??  :)  Honi soit qui mal y pense ....

> **Dr Small said:**
>  That was a nice sales pitch, by the way :) Talking of which ... Now that I think of it I could also have mentioned "Ubuntu One" ... that too would be "storage in the cloud".
[https://ubuntuone.com/](https://ubuntuone.com/)

---

### Post by hockey97 on 2009-08-16
So why is everyone going crazy about it? I have computer geek friends they know about computers but not on a technical scale.  They suggested me to update to latest ubuntu server edition. They talked about cloud computing.

To me, I rather own the items them rent/lease storage. I mean when you want to start a business you better have the cash to do so or else it's a amateur business. Something I say could easily crash down and never even make it. I  believe if you  buy your own equipment and  have at least 90% control on your operations then you can do so much and be flexable on the services you provide. I also do know about the real world business were competitors do dirty stuff behind the scenes like bribe your hosting provider to shut down your operations. I seen this stuff happen to many small businesses that use a hosting service provider.

Yet I do understand you have to balance cost with capital. I would rather struggle to have my own equipment and maintain it myself. If my operations get big enough I could always hire a person to maintain the equipment if needed too or if I don't want to employ a person. I can always contract the work outside. Their are contract houses where you can get a whole workforce to maintain your stuff it's cheaper in the sense of hiring the whole workcrew as your employees.

How would cloud computing differ from just a web hosting service?

---

### Post by jeffathehutt on 2009-08-16
> How would cloud computing differ from just a web hosting service?

Cloud computing can do more than a web host.  With cloud computing, you can actually 'rent' software without having to buy it.

This is a very dumbed down example, but say your new company needed to use photoshop to create some graphics for your web site.  One option, is to go out and buy windows (assuming your business runs linux), then go and buy photoshop and install it on windows.  That works, but it is also very expensive.

Now, suppose you have cloud computing.  You can 'rent' windows and photoshop for a month and pay much less for it.  Also, you don't have to go out and buy any physical products.  Everything is delivered over the network.

Obviously, most people wouldn't rent an entire operating system (assuming it was even possible), but one of the goals of cloud computing is to be os-independant.  It's very similar to the online google apps.  They work right through a web browser with no actual software to install on your computer.

I don't know much about cloud computing, so please correct me if I am wrong, but this is how I understand it right now.

---

### Post by ubuntwhat on 2009-08-16
Cloud computing is also good for saving money on hardware. You could own your own servers that host your cloud services, and then all of the other computers in your network can use the software that is on the cloud server. the server does all of the processing, computing, etc., and in turn you can buy cheaper hardware because it doesnt have to keep up with the demands of the software being ran. 
 
Google Cloud OS, its a cloud service that lets you run a whole operating system out of your browser.

---

### Post by scorp123 on 2009-08-16
> **jeffathehutt said:**
>  You can 'rent' windows and photoshop for a month and pay much less for it.  Also, you don't have to go out and buy any physical products.  Everything is delivered over the network.

Obviously, most people wouldn't rent an entire operating system (assuming it was even possible) ...  It is possible. You'd just need to use the right software, for example this one:
[http://www.sun.com/software/products/sgd/index.jsp](http://www.sun.com/software/products/sgd/index.jsp)

With this software I can deliver any OS I want onto your desktop. All you need on your end is a web browser with the Java plugin. That's it. Your client OS does not matter one little bit (you can run whatever you want on your end for as long as there is a web browser with a Java plugin).

You want to rent a Windows 7 desktop with Photoshop in it? I could do that and deliver it full-screen to you. You'd be sitting at your BSD, MacOS, Linux or whatever OS you have and be in a full-screen Windows 7 session delivered to you over the network, as if it was installed locally.

Voila. Cloud computing. And "software as a service".

---

