---
title: "Open Source Alternatives to GMail"
date: 2010-05-28
forum: The Cafe
---

### Post by LeifAndersen on 2010-05-28
I've been thinking for the past few days, everyone's been complaining about facebook, and my opinion has been: "it's your fault for trusting some random company on the internet with all of your private information, don't put information on the internet you don't mind the rest of the world seeing".

And then I got to thinking, what about Google, no one ever talks about that, and the amount of data we're giving Google for email.  I then think that it's not a big problem, because you're emailing people anyway, so it shouldn't really matter, after all, they could always go publish your mail...so it's just better to not say anything that could be incriminating over email as well.  Also, I'm sending unencrypted messages, so it's still technically wide open.

But then I start realizing that it's still a bad thing.  True, while no one at Google is reading my email (I think), who says that they will always be the 'good guys', which is to say, just like how everyone trusted facebook, and their motivations changed, nothing is preventing google from changing it's opinions.  And, even if Google keeps it's slogan, and never does become 'evil', they could still get subpoenaed, etc. etc.  In short, I'm saying I shouldn't trust this thing with the cloud.

So, this lead me to think, what is there out there besides GMail?  Sure, there is clients like evolution or thunderbird, but they fail short.  In particular, they don't really have threaded conversations.  Most of the other things I need (tags, filters, multiple email addresses), either come built in, or a solution can easily be hacked, but I haven't found any way to thread emails, and with the way I use email, I really need conversation threading.  Also, it would be nice if I could hide quotes by default...but I think there's a solution to do that.

Does anyone know of a good alternative to gmail that will thread conversations.  Preferably an open source solution.  I know outlook will do it for you.

Thank You.

---

### Post by pwnst*r on 2010-05-28
So other than hosting your own mail server, why would you trust an alternative?

---

### Post by LeifAndersen on 2010-05-28
Actually I do own my own mail server (well...I have it hosted, I don't actually own the hardware).  The only problem is that I don't use it, because I don't have a client that compares to gmail, so I end up using gmail.

---

### Post by markbahnman on 2010-05-28
I've been curious as well as to open source alternatives to gmail. When I found out about the Diaspora project I got thinking about getting open source alternatives to everything I use. Unfortunately I like gmail too much but I'd love to find a project to contribute to.

---

### Post by LeifAndersen on 2010-05-28
Okay, I just found out that evolution does have message threading, but rather than being in the preferences panel, it's located in the View drop down menu.  Apparently Thunderbird does the same thing.

I also tried out Zimbra, and other than that it appears to be based very heavily on java, it does look like it would also do the job, in addition, it's also really easy to configure (unlike evolution which requires you to know how email works to configure it, Zimbra's desktop client will let you simply put in you're credentials to any webmail based service, or to your own server, and it will set the rest up for you.  Although, it automatically downloads your mail, which could get annoying.

---

### Post by samalex on 2010-05-28
> **markbahnman said:**
> I've been curious as well as to open source alternatives to gmail. When I found out about the Diaspora project I got thinking about getting open source alternatives to everything I use. Unfortunately I like gmail too much but I'd love to find a project to contribute to.

I'm also watching Diaspora, but I don't think it'd be an alternative to Gmail, though it will hopefully replace Twitter and Facebook.

If I had the $$$ to buy my own hardware and colocate it, I'd setup a Zimbra server which is I think the next best thing to Google.  I'm not a huge fan of the Gmail web interface, so though I check it at work via the web I always connect through Pop3 and download the mail to my laptop so I can better organize the messages.  

I really just wish Gmail would be more like standard mail programs with folders because I don't like the 'tag' method they use.  Yeah it allows threading to work fairly well, but with thousands of emails (I've had my account since the first month Gmail started in 2004) it becomes really hard to organize if it wasn't done from day one.

Sam

---

### Post by Xbehave on 2010-05-28
[http://www.noupe.com/ajax/10-ajax-webmail-clients.html](http://www.noupe.com/ajax/10-ajax-webmail-clients.html)

I'd look at roundcube but you may prefer a different look.

---

### Post by markbahnman on 2010-05-28
> **samalex said:**
> I'm also watching Diaspora, but I don't think it'd be an alternative to Gmail, though it will hopefully replace Twitter and Facebook.
 
If I had the $$$ to buy my own hardware and colocate it, I'd setup a Zimbra server which is I think the next best thing to Google. I'm not a huge fan of the Gmail web interface, so though I check it at work via the web I always connect through Pop3 and download the mail to my laptop so I can better organize the messages. 
 
I really just wish Gmail would be more like standard mail programs with folders because I don't like the 'tag' method they use. Yeah it allows threading to work fairly well, but with thousands of emails (I've had my account since the first month Gmail started in 2004) it becomes really hard to organize if it wasn't done from day one.
 
Sam
 
I'm not familiar with Zimbra, are you able to set it up on your own server? I recently rented a low end dedi for experimenting with / a place to host my own Diaspora seed in the future. Always looking for new fun stuff to try and implement.

---

### Post by samalex on 2010-05-28
> **markbahnman said:**
> I'm not familiar with Zimbra, are you able to set it up on your own server? I recently rented a low end dedi for experimenting with / a place to host my own Diaspora seed in the future. Always looking for new fun stuff to try and implement.

Yup, [Zimbra Server]("http://www.zimbra.com/products/product_editions.html") has an open source edition that's completely free and honestly has all the features an individual or small business would want.  The licensed version has MANY more features, but unless you run a mid-sized to large shop it might be more than most would need.

The only downer is their installer is only for specific versions and distros.  Generally for Ubuntu they've stuck with LTS versions, which 10.04 is, but thus far they only have it for 6.04 and 8.04.  They do have the source you could download and build on your own, but I've read people having problems with that.

But if you have a server to put it in, it's awesome.  There's a web interface that rocks and Zimbra Desktop is a client-side app that looks great as well.  Personally I don't use it because I don't have a server at my disposal, but for the people and companies I know of who do use it, they love it.

From what I've seen and heard it's pretty much on par with enterprise mail servers like Exchange and Lotus Notes, so VERY powerful.

Sam

---

### Post by LeifAndersen on 2010-05-28
> **Xbehave said:**
> [http://www.noupe.com/ajax/10-ajax-webmail-clients.html](http://www.noupe.com/ajax/10-ajax-webmail-clients.html)

I'd look at roundcube but you may prefer a different look.

I did look at round cube, but I read that it was still very buggy.

---

### Post by pwnst*r on 2010-05-28
> **samalex said:**
> Yup, [Zimbra Server]("http://www.zimbra.com/products/product_editions.html") has an open source edition that's completely free and honestly has all the features an individual or small business would want.  The licensed version has MANY more features, but unless you run a mid-sized to large shop it might be more than most would need.

The only downer is their installer is only for specific versions and distros.  Generally for Ubuntu they've stuck with LTS versions, which 10.04 is, but thus far they only have it for 6.04 and 8.04.  They do have the source you could download and build on your own, but I've read people having problems with that.

But if you have a server to put it in, it's awesome.  There's a web interface that rocks and Zimbra Desktop is a client-side app that looks great as well.  Personally I don't use it because I don't have a server at my disposal, but for the people and companies I know of who do use it, they love it.

From what I've seen and heard it's pretty much on par with enterprise mail servers like Exchange and Lotus Notes, so VERY powerful.

Sam

Since the OP didn't bother replying to this, I'll say that it's very nice.  Personal and small businesses would indeed be perfect with this.  Our corporation uses Exchange, but I'm quite interested in this for a probable business venture.

Thanks for the post.

---

