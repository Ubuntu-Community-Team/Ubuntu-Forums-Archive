---
title: "(More) private search-engines and e-mail?"
date: 2012-04-09
forum: The Cafe
---

### Post by aykoola on 2012-04-09
So...

I've read about duckduckgo.com and ixquick.com being good private alternatives for google, so i would like to ask you guys if that's true.
+ i'd like to ask if there's a good gmail alternative?

Thank you!

---

### Post by lovinglinux on 2012-04-09
> **aykoola said:**
> So...

I've read about duckduckgo.com and ixquick.com being good private alternatives for google, so i would like to ask you guys if that's true.

Yes, it's true. [https://duckduckgo.com/privacy.html](https://duckduckgo.com/privacy.html)


> **aykoola said:**
> + i'd like to ask if there's a good gmail alternative?


Coincidently, I was looking for the same stuff today, since I am planning to get away from Google services.

Best mail service I could find is from the developers of Opera browser:

[https://mail.opera.com/](https://mail.opera.com/)

It is simple, elegant and lightening fast.


[IMG]http://i.imgur.com/9wXQZ.png[/IMG]


You can also retrieve your GMail accounts. Just enter the webmail, click "Settings" on the top-right corner, then "Account". Then fill the form with your GMail address and password. Initially, the setup only allows you to set the pop account, but when you click the button to add the account, it tells you it can't connect to smtp and the server field becomes accessible. Then try to add again and it will allow to change the port. 

If you use Opera browser, it integrates beautifully with the built-in mail reader. 

[http://www.opera.com/download/](http://www.opera.com/download/)

Configuration is automatic. All you need is to type the e-mail address and password to get a very nice IMAP service.

---

### Post by aykoola on 2012-04-09
thanks for the suggestion. 

but is it as private as duck is in the browser world?

Thank you again!

---

### Post by lovinglinux on 2012-04-09
> **aykoola said:**
> thanks for the suggestion. 

but is it as private as duck is in the browser world?

Thank you again!


Not exactly. 

[http://my.opera.com/community/terms-of-service/](http://my.opera.com/community/terms-of-service/)

> 3. MY OPERA MAIL PRIVACY

3.1 It is Opera's policy to respect the privacy of its members. Opera will not monitor, edit, or disclose any personal information about User or User’s use of the Service, including its contents, without User’s prior permission unless required or allowed by law, or where Opera has a good faith belief that such action is necessary to: (1) conform to legal requirements or comply with legal process; (2) protect and defend the rights or property of Opera; (3) enforce these Terms of service; (4) act to protect the interests of its members or others; or (5) facilitate a change of control of the Service or the acquisition of Opera's business by a third party and to enable that third party to continue to provide the My Opera Mail services to you. Opera may provide certain user information in aggregate form to third parties for demographics. In addition, User’s Internet protocol address is transmitted with each message sent from User’s account.

3.2 Opera may share email User reports as spam with third parties for the purpose of assisting in industry initiatives to control undesirable email. Information User provides to Opera may be stored outside of the country in which User resides, and User hereby consents to such storage and transfer of information between jurisdictions.

3.3 User agrees that Opera may access User’s account, including its contents, as stated above or to respond to service or technical issues. 

3.4 Opera’s Privacy policy is found at [http://www.opera.com/privacy](http://www.opera.com/privacy) and is hereby incorporated in these Terms of service.

---

### Post by aykoola on 2012-04-10
hmmm...

And Lavabit, for instance? Is it any good?

Thank you!

---

### Post by lovinglinux on 2012-04-10
See [https://en.wikipedia.org/wiki/Comparison_of_webmail_providers](https://en.wikipedia.org/wiki/Comparison_of_webmail_providers)

---

### Post by flurospar on 2012-04-10
You can use GPG to encrypt all your mail, though! That way, no one could read your mail (unless, of course [this happens]("http://imgs.xkcd.com/comics/security.png")), irrespective of whichever service you use.

---

### Post by Linux_junkie on 2012-04-10
For secure email you could try [hushmail]("http://www.hushmail.com/")

---

### Post by Nimless on 2012-04-10
Make your own mail server or hire someone that can do it :p

---

### Post by bedpotato on 2012-04-10
> **Linux_junkie said:**
> For secure email you could try [hushmail]("http://www.hushmail.com/")

A Hushmail account comes with a mere 2MB of storage (unless you're willing to pay to upgrade).

:(

---

### Post by Dry Lips on 2012-04-10
I usually recommend using Lavabit + Thunderbird/Enigmail (=PGP encryption).

---

### Post by aykoola on 2012-04-10
> **Dry Lips said:**
> I usually recommend using Lavabit + Thunderbird/Enigmail (=PGP encryption).

OK, did just that :)

I bought a no-ad subscription for one year :)

Now i made a canned response on my gmail account, so people get redirected to my new email adress. After two weeks or so i'll completely delete my google profile.

---

### Post by user1397 on 2012-04-11
> **lovinglinux said:**
> Coincidently, I was looking for the same stuff today, since I am planning to get away from Google services.May I ask your reasoning to get away from google services?  (just curious, as I have been thinking about this for a while now).

Also, using opera mail? Do you also use the opera browser?! Blasphemy you firefox add-on developer! :guitar:

---

### Post by ikt on 2012-04-11
[http://xkcd.com/538/](http://xkcd.com/538/)

;)

Your emails aren't that interesting to read anyway...

---

### Post by lovinglinux on 2012-04-11
> **ubuntuman001 said:**
> May I ask your reasoning to get away from google services?  (just curious, as I have been thinking about this for a while now).

It is a long story, but essentially because of the recent deal between Google and Adobe, that will transfer development of Flash for Linux to Google, which will implement PepperFlash. It looks like, to me, as a move from Google to force adoption of Pepper API, since both Mozilla and Opera are against it. Furthermore, I see no reason for Google to start developing PepperFlash, when it should be focusing on the adoption of WebM and HTML5. It has been 2 years since the acquisition of VP8 and YouTube still heavily depends on Flash. Not to mention the whole deal about Google announcing the removal of h.264 support from Chrome, which still exists one year later.

Look at their statement about removing h.264 support:

[http://blog.chromium.org/2011/01/html-video-codec-support-in-chrome.html](http://blog.chromium.org/2011/01/html-video-codec-support-in-chrome.html)

> We expect even more rapid innovation in the web media platform in the coming year and are focusing our investments in those technologies that are developed and licensed based on open web principles. To that end, we are changing Chrome's HTML5 <video> support to make it consistent with the codecs already supported by the open Chromium project. Specifically, we are supporting the WebM (VP8) and Theora video codecs, and will consider adding support for other high-quality open codecs in the future. Though H.264 plays an important role in video, as our goal is to enable open innovation, support for the codec will be removed and our resources directed towards completely open codec technologies.

Now they are investing in a proprietary technology, using a self-developed API that nobody wants and becoming the only browser vendor in the Linux market to distribute updated versions of flash.

I never liked Chrome. Now I am scared of what could happen if Chrome dominates the browser market. So, I won't help Google anymore if I can.

BTW, Mozilla recently decided to support h.264 to continue to stay relevant in the mobile market. They opened a scary precedent.

> **ubuntuman001 said:**
> Also, using opera mail? Do you also use the opera browser?! Blasphemy you firefox add-on developer! :guitar:

You don't need Opera browser to use their mail service, but yes, I use Opera browser as well.

---

### Post by aykoola on 2012-05-11
what about this search engine:

[http://blekko.com/](http://blekko.com/)

is it also private?

---

### Post by MisterGaribaldi on 2012-05-11
> **lovinglinux said:**
> [QUOTE=ubuntuman001;11835855][QUOTE=lovinglinux;11832116]Coincidently, I was looking for the same stuff today, since I am planning to get away from Google services.

May I ask your reasoning to get away from google services?[/quote]

It is a long story, but essentially because of the recent deal between Google and Adobe... <snip>[/quote]

Huh? Sorry, I tried real hard, but I do not understand (or perhaps "see") the relevance between your actions and your reasoning.

---

### Post by ubuntu27 on 2012-05-11
Nothing can beat [Lavabit]("https://lavabit.com/") for e-mail.

---

### Post by aykoola on 2012-05-12
> **aykoola said:**
> what about this search engine:

[http://blekko.com/](http://blekko.com/)

is it also private?

anyone?

---

### Post by zombifier25 on 2012-05-12
> **aykoola said:**
> anyone?

Maybe, but I still prefer duckduckgo since it's really powerful and fast.

---

### Post by lisati on 2012-05-12
> **aykoola said:**
> 
+ i'd like to ask if there's a good gmail alternative?

I run my own, based around Postfix, with spam and AV checking. I can access it via webmail, IMAP and POP3, and very little spam makes it through.

---

### Post by lovinglinux on 2012-05-12
> **MisterGaribaldi said:**
> Huh? Sorry, I tried real hard, but I do not understand (or perhaps "see") the relevance between your actions and your reasoning.

[LIST]
[*]Google recent moves shows me they are more interested in boosting their products and promoting their technology than making a better web
[*]I don't want to contribute to Google machine anymore
[*]I am cutting my dependency on Google products
[/LIST]

BTW, I am very satisfied with My Opera Mail.

---

### Post by kdane4 on 2012-05-12
> **lovinglinux said:**
> 

Best mail service I could find is from the developers of Opera browser:

[https://mail.opera.com/](https://mail.opera.com/)


Thank you for mentioning this, I just registered and I really like the simplicity.. :)

---

### Post by lovinglinux on 2012-05-12
> **kdane4 said:**
> Thank you for mentioning this, I just registered and I really like the simplicity.. :)

You are welcome. It is incredibly fast and has all the features I need. Feels like using a desktop app without the clutter. I am really satisfied with it.

---

