---
title: "Server-side Javascript - Adsense"
date: 2010-02-01
forum: Server Platforms
---

### Post by xbaez on 2010-02-01
Is there any application that I can use in order to compile Adsense on the server?

Too many users are using NoScript now a days and they can block pretty much 100% of my advertisers, and I have no idea how to detect that

I can block Adblock and NoScript, but again, using NoScript, users can allow domain.com and disallow google.com

it's pretty easy for them

Here is a couple of programs that I tried:
```

ejs simple.html
ejs: Error: ReferenceError Exception: document is not defined
Stack:
 [00] simple.html, global, line 1 -> document.writeln("<br>\n");

jsext simple.html
Line 1 in ./simple.html:ReferenceError: document is not defined
```

the code of the simple.html is this:
```
document.writeln("<br>\n");
document.writeln("Hello World!");
```

Is there a command line browser with JavaScript support or something like that?

---

### Post by BkkBonanza on 2010-02-01
What are you trying to achieve here? You want to run the Adsense js code on your server and insert the result into your page? I'm about 99% sure that would be against Adsense terms of use even if you could do it. It would remove any way for Google to know that your ad serving and click-thrus are not completely fabricated since you could just as easily generate the click-thrus. They depend on the client IP for tracking and verification so this idea is a total non-starter. You would be terminated almost as soon as you tried this (all your page views would originate from your own IP).

User's have the right to block content on their machine - you just have to live with that. On the whole I think it's a small minority that do block ads. 

Besides which, you'll have to learn a lot more about using javascript code in - you can't just put it in the html code like you tried above. There is server-side javascript interpreters you can use but I haven't worked with them.

Edit: If you consider ad viewing mandatory for your users then you could add code to detect when ads are blocked and let users know they need to enable them to be able to use your site. That's an option but be prepared for visitors to just leave.

---

### Post by xbaez on 2010-02-01
> **BkkBonaza said:**
> What are you trying to achieve here? You want to run the Adsense js code on your server and insert the result into your page? I'm about 99% sure that would be against Adsense terms of use even if you could do it. It would remove any way for Google to know that your ad serving and click-thrus are not completely fabricated since you could just as easily generate the click-thrus. They depend on the client IP for tracking and verification so this idea is a total non-starter. You would be terminated almost as soon as you tried this (all your page views would originate from your own IP).

User's have the right to block content on their machine - you just have to live with that. On the whole I think it's a small minority that do block ads. 

Besides which, you'll have to learn a lot more about using javascript code in - you can't just put it in the html code like you tried above. There is server-side javascript interpreters you can use but I haven't worked with them.

Edit: If you consider ad viewing mandatory for your users then you could add code to detect when ads are blocked and let users know they need to enable them to be able to use your site. That's an option but be prepared for visitors to just leave.

You are one of those persons that just makes critiques

I never said I want to auto-fabricate clicks, where do you get that conclussion???

If you are a webmaster (like me), you pay your rent with Advertising

Adblock and NoScript are your 2 worst enemies, since 25%, 50% of your users can be navigating through your site without watching publicity

With that said, I googled a lot and found a way to achieve that

So if a use is not blocking Adsense from being displayed, a message will appear

---

### Post by ICEB3AR on 2010-02-01
I aggree with BkkBonaza and would like to add....

If you really need your advertisement then just improve your site and make it not be seen by users who have no javascript enabled. And just let they access if they are bots like google or if they have enabled js. 

Else just look for another way to get money for advertisement like with pictures instead of js code.

---

### Post by badSheep8 on 2010-02-01
> **xbaez said:**
> You are one of those persons that just makes critiques

I never said I want to auto-fabricate clicks, where do you get that conclussion???

If you are a webmaster (like me), you pay your rent with Advertising

Adblock and NoScript are your 2 worst enemies, since 25%, 50% of your users can be navigating through your site without watching publicity

With that said, I googled a lot and found a way to achieve that

So if a use is not blocking Adsense from being displayed, a message will appear

I'm a web master and don't need ads to pay my web host rent.

Actually I'm one of those who will do anything to block scripts like Adsense to protect my privacy. Adblock and NoScript are my biggest friends.

WTF: why is "http://yui.yahooapis.com/2.7.0/build/yahoo-dom-event/yahoo-dom-event.js?v=384" needed??

---

### Post by BkkBonanza on 2010-02-01
Actually, I never accused you of wanting to create ad clicks. I said that Google would not accept you forging ad content on your server because you ***could*** create ad clicks. I never said you WANTED to do that. You are being overly defensive. I was just pointing out why this type of approach would not be acceptable use for Google and that some other approach is needed. Judging by your writing I'm guessing you just mis-understood my English.

If you found a way to force users to view ads then good for you. That is going to work better than a server side workaround. I really doubt that more than 10% of users surf with ad blocking software. I've never seen any stats though.

---

### Post by badSheep8 on 2010-02-01
I just checked out your website. I don't think it's nice of you to pluck content and reviews of other websites and put them on your own website and just putting a plain text link (not enclosed in html tags) to the original website. People would have to copy - paste the URL in their browser to see the real website that had the content.

So while you're trying to force people to see your ads, you are stealing add clicks from others!

---

### Post by xbaez on 2010-02-01
> **badSheep8 said:**
> I'm a web master and don't need ads to pay my web host rent.

Actually I'm one of those who will do anything to block scripts like Adsense to protect my privacy. Adblock and NoScript are my biggest friends.

WTF: why is "http://yui.yahooapis.com/2.7.0/build/yahoo-dom-event/yahoo-dom-event.js?v=384" needed??

Well, good for you 

I've been paying my bills 10 years thanks to ads

I was able to see if users have loaded the google_frame1

if they don't, then I display them a message

same with the doubleclick ads

I would rather have 60% of my visitors, all watching ads, that my server over load with people with no advertisement

You can try your Adblock and your NoScript tools on my site, they won't work :)

---

### Post by xbaez on 2010-02-01
> **badSheep8 said:**
> I just checked out your website. I don't think it's nice of you to pluck content and reviews of other websites and put them on your own website and just putting a plain text link (not enclosed in html tags) to the original website. People would have to copy - paste the URL in their browser to see the real website that had the content.

So while you're trying to force people to see your ads, you are stealing add clicks from others!

Shut Up
show me your website and let's compare

I have had meetings with both IGN and GameSpot

again

I asked for HELP DAMMIT

and people like you, go to my website, and critique my work?

If you don't want to help, then shut up man, if you want to insult my work, do it in a private message

I couldn't care less about your opinion

---

### Post by xbaez on 2010-02-01
> **BkkBonaza said:**
> Actually, I never accused you of wanting to create ad clicks. I said that Google would not accept you forging ad content on your server because you ***could*** create ad clicks. I never said you WANTED to do that. You are being overly defensive. I was just pointing out why this type of approach would not be acceptable use for Google and that some other approach is needed. Judging by your writing I'm guessing you just mis-understood my English.

If you found a way to force users to view ads then good for you. That is going to work better than a server side workaround. I really doubt that more than 10% of users surf with ad blocking software. I've never seen any stats though.

Hey bro here is the code:

<body>
<?include ("/path/to/google/300x250.html");
<script>
// Anti-Ad Blocking.
var adsOn = document.getElementById('google_ads_frame1');
if(adsOn == null) {
        document.write("Noscript detected. Please allow Google ads");
    // Ads not loaded..
    // Continue what to do here, IE: Show message, redirect etc.
}
</script>
</body>


I hope the moderators can close this thread since all I have is haters saying going against my site

I've always wonder why people have time to go to the internet and start insulting others


I find every critique bout my website very insulting, these are not positive constructions, just punks running their mouth because they have nothing else to do

haters

---

