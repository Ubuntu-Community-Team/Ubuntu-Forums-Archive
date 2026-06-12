---
title: "stupid questions-adding users and server security"
date: 2007-03-22
forum: Server Platforms
---

### Post by wolfear on 2007-03-22
This will probably be one of the dumbest series of questions ever. I think I am brain dead today.

I just did a reload of my system (no real reason other than I wanted to play with various different configurations while I had some down time).
The base install is Edgy server and I used the "Perfect Server" from HowtoForge out of curiosity. Since I will also use the same box for work ( I only have the one system which is why I need a desktop), I added the Kubuntu desktop on it since I really like some of the available tools.
Anyway, I have used LAMP locally for quite a while, but the situation has arisen during this process, that I now need to allow access from an XP machine in another city (I just do code. Someone with actual taste will be doing the front-end designs).
I am sitting behind a 2wire modem and have no problems opening ports to allow access and a DLink switch (NOT a router. The 2wire handles that just fine). I have already gotten an account from DynDNS for a "static" IP since our modem gets re-assigned about once a month and ddclient is up and running.

Now for the stupid questions:
What is the best way to secure this server so that only my partner (and maybe occasionally a client) can access the files to view via browser and ftp when needed?
She doesn't need direct MySQL access, just the ability to access files via ftp (since her software has the ability built in), edit, upload, and view and clients only need the ability to view.
My partner would have no clue what ssh is (not that I really do either).
I have added a "public" folder to  /var/www  in order that /var/www retains its default settings and only the "public" directory would need to be accessible from the internet.
The HowTos and other posts been wonderful and everything is running great, but none seem to quit cover how to allow specific "per user" type of access without adding some overkill like ISPConfig or something simliar.
I know how to add a user to my system, but that is not, I don't think, what I need to do. I could be wrong.

As an aside, I would like to, possibly, theoretically if I can learn how, someday, add an IRC and a SILC server if that affects anything now.
I have been reading too long today and my brain is mush.

---

### Post by kidders on 2007-03-22
Hi there,

Sounds like you have a nice setup. :-)

> **wolfear said:**
> What is the best way to secure this server so that only my partner (and maybe occasionally a client) can access the files to view via browser and ftp when needed?To be honest, exposing files via HTTP & FTP just isn't safe. If it were me, I would...

[LIST]
[*]Give anyone who needed to actually edit things SSH access to my box.
[*]Open port 22, and take appropriate precautions (below).
[*]Open port 80, so people can view your web pages.
[*]Close all other ports.
[/LIST]

The way your o/p is phrased almost makes it sound like you want to restrict HTTP access to specific people. There are a great many ways of doing this ... if it's something you need to do, I'd be happy to outline the major ones.

> **wolfear said:**
> She doesn't need direct MySQL access, just the ability to access files via ftp (since her software has the ability built in)Personally, nothing could make me run an FTP server for any more than a few minutes at a time on my box, unless I just didn't care about the safety of what was being transferred. SFTP (or at least FTPS) would be better.

> **wolfear said:**
> As an aside, I would like to, possibly, theoretically if I can learn how, someday, add an IRC and a SILC server if that affects anything now.These are relatively straightforward things to do... seen one server, seen em all. :-) If you can install Apache, you can install IRC hehe.

There's nothing terribly odd that you need to accommodate *now* though, so no need to worry.

**_A note about "appropriate precautions"_**
Using dynamic DNS services often seems to attract unwanted attention to your box, so it's important to watch how the services on open ports are being used. Don't serve _anything_ that could allow modifications to your system, without authentication & encryption, and take steps to automatically block people who misbehave.

> **wolfear said:**
> This will probably be one of the dumbest series of questions ever. I think I am brain dead today.None of your questions is stupid! Your post was detailed & helpful. :-)

---

### Post by wolfear on 2007-03-22
Kidders,
Thank you soooo much. I thought I had till sometime next week to get things sorted out, but, as it turns out I don't. 

> **kidders said:**
> 
To be honest, exposing files via HTTP & FTP just isn't safe. If it were me, I would...

[LIST]
[*]Give anyone who needed to actually edit things SSH access to my box.
[*]Open port 22, and take appropriate precautions (below).
[*]Open port 80, so people can view your web pages.
[*]Close all other ports.
[/LIST]


Problem is, my partner is a great designer, but has limited computer knowledge and no concepts of security beyond running AV/AS scans. We had the devil's own time just getting her working via FTP with hosted servers.
In order to facilitate our coordination, we are both going to be using PHPDevelopment Studio (which I will probably be installing and configuring remotely on her XP machine) and since it has the available FTP utility, she would be using that for accessing various servers.
If it were strictly clients, I would leave the ports closed until needed, but she works at odd hours of the day or night so opening and closing port or starting and stopping services isn't practical.
> **kidders said:**
> 
The way your o/p is phrased almost makes it sound like you want to restrict HTTP access to specific people. There are a great many ways of doing this ... if it's something you need to do, I'd be happy to outline the major ones.


That is exactly what I need to do. "Unlimited" (so to speak) access for my partner and then a method of allowing clients to view work at various phases during the development (Preferably, I would want to manually allow them "read only" access to their specific directory to keep out the nosy types, but it's not required).

> **kidders said:**
> 
Personally, nothing could make me run an FTP server for any more than a few minutes at a time on my box, unless I just didn't care about the safety of what was being transferred. SFTP (or at least FTPS) would be better.

When I was following the "Perfect Setup" How-to, I installed Proftpd with sasl and tls, would this work?
I'm still new to the many different security and authentication mechanisms available since I mostly deal with the web where just about everything is done via password and/or visual verifications, so feel free to correct me if I misunderstood what those are for.

> **kidders said:**
> 
**_A note about "appropriate precautions"_**
Using dynamic DNS services often seems to attract unwanted attention to your box, so it's important to watch how the services on open ports are being used. Don't serve _anything_ that could allow modifications to your system, without authentication & encryption, and take steps to automatically block people who misbehave.

Yes, that is why I haven't opened anything to the outside yet. I was playing around some things a while back and opened up a few ports on my modem and got slammed. Nothing bad happened, but it made me frighteningly aware of the danger..hence my questions.

I want to thank you again. Your input has already been very helpful.

---

### Post by kidders on 2007-03-22
Hey again,

> **wolfear said:**
> We had the devil's own time just getting her working via FTP with hosted servers.Ah. Well, if you really want to use FTP, securing it with TLS like you mentioned is essential. I would still very strongly recommend SSH though ... Shell access offers far more flexibility than a simple file transfer interface.

I would recommend:[LIST]
[*]Binding the FTP server to a non-standard port, to make it slightly less obvious you're running it.
[*]Throwing something together to block anyone who repeatedly fails to authenticate.
[/LIST]

> **wolfear said:**
> That is exactly what I need to do. "Unlimited" (so to speak) access for my partner and then a method of allowing clients to view work at various phases during the development (Preferably, I would want to manually allow them "read only" access to their specific directory to keep out the nosy types, but it's not required).Would it be possible to show clients everything they wanted to see over HTTP?

If it were me, I would consider writing a quick script to let clients wander around source trees, and view stuff like PHP code in a pretty, styled-up way. That way, they could see their site *and* the underlying source, without using FTP. Then, you could use client-side certification to manage access restrictions. You could issue your clients with digital certificates that would allow them access to their own data.

In more detail...

[LIST]
[*]Imagine you have https://www.totallyamazingwebdevelopers.com/, and dedicated subdomains for each of your clients, for use while their sites are stored on your system.
[*]I hire you to do some work, which you store at /var/www/**kidders**, exposed to the world as https://**kidders**.totallyamazingwebdevelopers.com/.
[*]You and your web developers have unrestricted FTP access to everything in /var/www/. Similarly, you each have digital certificates that will let you into all of your subdomains over HTTP.
[*]You issue me with a cert that lets me see https://kidders.totallyamazingwebdevelopers.com/, and take a look around.
[*]Using URL rewrites, you give me https://kidders.totallyamazingwebdevelopers.com/source/ to let me view the directory structure, and read the source of server-side scripts.
[/LIST]

How close would that come to what you require?

> **wolfear said:**
> I was playing around some things a while back and opened up a few ports on my modem and got slammed.Yeah... you have to be careful what you serve! This is one of the reasons I thought of client-side certification. Aside from the fact that you won't have to keep reminding clients what their passwords are, people can "slam" your web server all they like ... if there's no password to guess, it makes things a bit harder for them!

> **wolfear said:**
> I want to thank you again. Your input has already been very helpful.No problem. :-)

There are also some other options for authentication over the web, including "simple" HTTP authentication, and session-based (ie requiring a login) options. You *could* also use IP-based access restrictions ... but that might be a bit impractical.

---

### Post by wolfear on 2007-03-22
> **kidders said:**
> 
Ah. Well, if you really want to use FTP, securing it with TLS like you mentioned is essential. I would still very strongly recommend SSH though ... Shell access offers far more flexibility than a simple file transfer interface.

I would recommend:[LIST]
[*]Binding the FTP server to a non-standard port, to make it slightly less obvious you're running it.
[*]Throwing something together to block anyone who repeatedly fails to authenticate.
[/LIST]

For now, using ftp beats trying to teach someone who is the "point->click->call me for tech support" type, a new technology facet.
Thanks for the non-standard port suggestion. That is one I will definitely use.

On the authentication blocking, I read on the forums, I think it was yesterday, something about "tripwire" but didn't really read much more as it was incidental to what I was searching for. Is that similar to what you are suggesting?

> **kidders said:**
> 
Would it be possible to show clients everything they wanted to see over HTTP?

If it were me, I would consider writing a quick script to let clients wander around source trees, and view stuff like PHP code in a pretty, styled-up way. That way, they could see their site *and* the underlying source, without using FTP. Then, you could use client-side certification to manage access restrictions. You could issue your clients with digital certificates that would allow them access to their own data.

[LIST]
[*]Imagine you have [https://www.totallyamazingwebdevelopers.com/](https://www.totallyamazingwebdevelopers.com/), and dedicated subdomains for each of your clients, for use while their sites are stored on your system.
[*]I hire you to do some work, which you store at /var/www/**kidders**, exposed to the world as [https://**kidders](https://**kidders)**.totallyamazingwebdevelopers.com/.
[*]You and your web developers have unrestricted FTP access to everything in /var/www/. Similarly, you each have digital certificates that will let you into all of your subdomains over HTTP.
[*]You issue me with a cert that lets me see [https://kidders.totallyamazingwebdevelopers.com/](https://kidders.totallyamazingwebdevelopers.com/), and take a look around.
[*]Using URL rewrites, you give me [https://kidders.totallyamazingwebdevelopers.com/source/](https://kidders.totallyamazingwebdevelopers.com/source/) to let me view the directory structure, and read the source of server-side scripts.
[/LIST]

How close would that come to what you require?


Clients will only need to view designs as seen from the web, since viewing the underlying code is not something they want or need to worry about, but I do see what you are getting at and I REALLY like the certificate idea.
I would never have thought of that.
Would that be done using OpenSSL or something and how would it need to be implemented on the client end?
Most of the people we deal with are doing good to push a power button correctly.
:lolflag: 

I am really liking your suggestions, and I guess if you could point me in the right direction, I can follow a set of docs. from there.

Your input has been invaluable. I can't thank you enough.

---

### Post by kidders on 2007-03-22
> **wolfear said:**
> On the authentication blocking, I read on the forums, I think it was yesterday, something about "tripwire" but didn't really read much more as it was incidental to what I was searching for. Is that similar to what you are suggesting?Yes, but far more elabourate. I was really only referring to something you might throw together yourself in 5 minutes. Although there's nothing *wrong* with installing robust security & intrusion detection applications, you probably wouldn't consider it necessary.

> **wolfear said:**
> I REALLY like the certificate idea. I would never have thought of that. Would that be done using OpenSSL or something and how would it need to be implemented on the client end?You've got the idea alright... Setting Apache (assuming you're using it) up to require client-side certification is almost trivial.

Like you suggested, you would use OpenSSL to generate all the certificates. With a little thought, I'm sure you could reduce setting up a website & certification for a new client to a single command, for convenience. Client-side, the only wrinkle would be that anyone using your certificates would have to install your root cert, since I doubt you'd want to pay Verisign/etc. for a "real" one. Essentially, the only difference between you and any other certificate-based service would be that peoples' browsers wouldn't trust your CA by default.

So, how to point you in the right direction? Hmmmm...

Let's make things complicated, and assume you only have one IP (which, as you may know, limits your options when dealing with SSL, because you can't have multiple virtual hosts). I would do something like the following:

**Ground work**
Let's assume /var/www contains a list of directories, each corresponding to a virtual host. One of them might be your company website. You would add another for your new secure service ... let's call it /var/www/secure. (Its configuration might be at /etc/apache2/sites-available/secure.) Below that, you'll have one directory per client, so mine might be /var/www/secure/kiddders. I would access it from https://secure.totallyamazingwebdevelopers.com/kidders/.

The Apache configuration for the secure.totallyamazingwebdevelopers.com virtual host would *enable* support for SSL & client certification, but not do much more than that. You might find the "CompatEnvVars" and "StdEnvVars" **SSLOptions** directives of particular interest, since they make certificate-related information available to scripting engines like PHP.

Google searches like [this one](http://www.google.com/search?hl=en&q=apache+SSLVerifyClient+howto) will give you an idea for the kind of thing you'd be dealing with.

Step one would be to successfully configure Apache to host a "hello world" page on an SSL service, and configure your browser so it trusts the issuer of your digital certificate.

**Setting up new clients**
Now, you could start thinking about what you might need to do, every time you take on a new contract. Rough example:

[LIST=1]
[*]Create a place to put files: **mkdir /var/www/secure/kidders**
[*]Install your usual back-end template: **tar -xf /opt/webdesign/template.tar /var/www/secure/kidders**
[*]Tweak all the permissions: **chown -R whoever:whatever /var/www/secure/kidders**, and so on.
[*]Create an encryption key for a new client: **openssl genrsa -des3....** (Knowledgeable clients may prefer to hand you one of their own.)
[*]Create a request for a new client certificate: **openssl req -new....** (Again, knowledgeable clients may prefer to hand you one of their own.)
[*]Sign the certificate: **openssl ca....**
[*]Convert the certificate into something stupid (ie Microsoft) computers won't bawk at: **openssl pkcs12 -export -clcerts....**
[*]Email the certificate to your client: **sendmail whoever@wherever.com....**
[*]Create a corresponding **.htaccess** file
[/LIST]

That last step is the most important. You would take your Apache configuration from the general to the specific on a per-directory basis, by writing out .htaccess files that explicitly state which certificate holders are allowed to traverse each directory tree. The **SSLRequire** and **SSLVerifyClient** directives will help you there.

After one successful manual execution, you should have all you need to write a shell script to do the next one *for* you.

**Client-Side**
Clients would install your root certificate and their own client certificate, so they'll be accessing a web server certified by a trusted authority using a cert signed by the same people, and everything will be peachy. For me (on my Mac) that would be a matter of double-clicking both files. (On Linux, it's never quite so simple!)

Now, thanks to my personal .htaccess file, when I try to access https://secure.totallyamazingwebdevelopers.com/kidders/, I'm admitted, but not if I try to peek at somebody else's stuff. My cert would be set to expire after, say, 28 days, beyond which, your server would reject my access attempts outright.

Thinking about things from a security perspective for a second, the first thing worth noting is that you can't use the "non-standard port" trick to throw malicious users off the scent with this service. Since clients will most likely want to access it from corporate environments & other proxied connections, local restrictions may not permit outgoing access on ports other than 80 and 443.

Since you're not authenticating by password, the worst case scenario would be (a) someone manages to acquire one of your client certs, (b) they use it before it expires, (c) they know it came from your web server, and (d) they guess the right URL from the original client's name. In those circumstances, your security would fail.


Anyhow, sorry for rambling... I hope this points you where you need to go. If you still have questions though, feel free to post them.

---

### Post by wolfear on 2007-03-22
WOW!
You go right ahead and ramble anytime you want...lol.
This does indeed give me a great starting point. I'm printing this all out so I can have it in front of me while I go through it. Should keep me busy for a few days.

To give you an idea of the types of people I normally deal with and why the client end is so vital it be simple (You will love this one):
Got an IM this evening from my partner, who also does some work for a local insurance company. The owner just bought a new laptop with an AirCard so it can be used in the field for claims.
The owner then buys a new printer which is supposed to be "wireless network compatible". Here is a sample of the conversation (I changed the names):

partner: what do you think?
me: explain to me one more time exactly WHERE the printer is being plugged into the network
partner: it is NOT plugged in ......... is supposed to be wireless
me: it has to plug into something. it can't just sit on a counter and run
partner: nope............
partner: wireless
partner: this is a Toshipa laptop w/VISTA  and HP 8160c all-in one printer
partner: the laptop has a wireless card which gets inserted into laptop
me: oh jeez...do you see anyplace to put a wireless card on that printer???!!!
partner: I thought is was built in???

Needless to say after a bit more sarcasm, we finally got them straightened out.
:lolflag:

Once more, thank you so much for your help. Ill post back here in a few days and let you know how things are progressing.

---

### Post by airtonix on 2007-03-26
seriously....ssh is way easier than securing ftp....plus your XP user can still use  an ftp client(just has to support sftp). the ftp client "filezilla" does this.

to install ssh : 

```
sudo apt-get install openssh-server
```

ok now joe wants to upload his work for you to /var/www/joes-work/

so you create a user account for joe ( gui way if you want )

then create a public_html folder under his home folder, chmod it 775

symlink the folder to the /var/www and rename the symlink in /var/www to joes-work.

tada! when joe logs onto the ssh-server(sftp-server) the folders and files they see will be there home folder, plus this public_html folder. tell them to put the data into the public_html folder.

then you can also see these files at [http://your-ip-address/joes-work](http://your-ip-address/joes-work)

---

### Post by wolfear on 2007-03-27
airtonix-
I do appreciate all the input.
One reason I am stuck on ftp is due to software considerations.
PHP Development Studio, which is the platform we are using, is based on Eclipse and, if I am understanding everything I read, Eclipse does not handle ssh gracefully.
However, it does have an ftp module which I have used with little problem in the past, and my partner is used to working with ftp (not great, but she can use it).
This is strictly for co-ordinating development work and allowing for client reviews at various phases.
There are no domains hosted as I have a separate managed server for that, so the www directory is currently organized by client and/or project, not by user.

As thing progress and my partner becomes more knowledgeable (I think she is just about ready to dump XP and go with Ubuntu since there are some tools she wants which are not available on M$), we may change things.

Once again, thank you for the input. Everything is being taken into consideration.

---

