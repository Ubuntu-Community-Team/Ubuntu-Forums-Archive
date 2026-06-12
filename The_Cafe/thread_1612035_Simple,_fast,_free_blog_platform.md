---
title: "Simple, fast, free blog platform"
date: 2010-11-02
forum: The Cafe
---

### Post by siddartha on 2010-11-02
I keep a daily low traffic blog (100-180 access a day) which is rather small - only text and links, no multimedia whatsoever, not even pictures or fancy round cornered buttons. What I need is an advanced queue or as I've seen it in other places automatic post scheduler to manage the already written posts so they are published each at a certain hour, 24 hours after the latest published entry. The queue should be flexible in case some posts are reprioritised and are put higher on the list.

Already had something like that on thumbler, but the unreliability of the service, the constant stream of downtime and the fact that their platform takes every possible step to lock the subscribers in by not having even the most basic export functions and just a beta backup tool for mac... well, that's reason enough to try and move the whole content sooner than later (over a year of activity).

I am looking for a free platform and hosting. I had been adviced to look for blogger or wordpress. Both are cute, but all they have is a scheduler which makes hard to administer a longer list of unpublished material. So what else do you know out there? I need to be able to tweak and optimise the theme (if there's only text, why waste time on useless bells and wistles?). Also I have to be able to insert javascript as for google analytics like functionality and disqus comments or some meta tags for Facebook integration.

Is there anything like that out there or only sites that make reposting easier?

---

### Post by juancarlospaco on 2010-11-02
Use Python.

---

### Post by siddartha on 2010-11-02
> **juancarlospaco said:**
> Use Python.
Hahahaha
It's like asking for a lift to the next town and getting an answer like "find a hammer and some wood mate". Cute.

---

### Post by Quadunit404 on 2010-11-02
The only one I can think of right now is WordPress, which you already mentioned, as I use that.

I like it because there's a [plugin that replaces the 404 page with a BSOD.]("http://wordpress.org/extend/plugins/bsod/") No other blogging platform's gonna let you do that TMK.

---

### Post by juancarlospaco on 2010-11-02
*What?, Python can do web things too...*

---

### Post by The Real Dave on 2010-11-02
I use and love Wordpress on Wordpress.com free hosting, but you've already looked into that. 

[Posterous]("https://posterous.com/") is  a nice and simple blog platform, you simply send an email, and your message turns into a blog post. You could perhaps use an email client (Evolution) to send the emails at certain times, or even use a command line client, and schedule a job with cron.

That said, I'm stabbing in the dark here.

---

### Post by lisati on 2010-11-02
I, too, thought of Wordpress, which can be [configured]("http://codex.wordpress.org/Post_to_your_blog_using_email") to turn an email into a blog post. I haven't checked out the scheduling side, but suspect it could be done through a cron job. "Blog entry poster" can also be used to post to it.

Thanks, Quadunit404, on the heads-up on the 404 plugin - looks promising.

---

### Post by JBAlaska on 2010-11-02
I have no experience with it, but you might check out:
[http://en.over-blog.com](http://en.over-blog.com)

---

### Post by siddartha on 2010-11-02
> **Quadunit404 said:**
> I like it because there's a [plugin that replaces the 404 page with a BSOD.]("http://wordpress.org/extend/plugins/bsod/") No other blogging platform's gonna let you do that TMK.

Yea, queue management is the reason for a few plugins, markup is also a posibility once you have the plugins, yet the wordpress.com does not allow that. And I have no idea how to get a customised wordpress up and running on a free service that works (I already have tumblr for that - it does not work and has often problems with the post queue).

> **juancarlospaco said:**
> *What?, Python can do web things too...*
Yes. That is very true. And a hammer is an essential tool if you are planning to build your own means of locomotion like a car, buggy or even a train.

> **The Real Dave said:**
> I use and love Wordpress on Wordpress.com free hosting, but you've already looked into that. 

[Posterous]("https://posterous.com/") is  a nice and simple blog platform, you simply send an email, and your message turns into a blog post. You could perhaps use an email client (Evolution) to send the emails at certain times, or even use a command line client, and schedule a job with cron.

That said, I'm stabbing in the dark here.
Wordpress is so nice, it has so many features, yet the free hosting has too many limitations. Also I've read about some ugly security issues some time ago with wordpress, although maybe any CMS would bump into such problems sooner or later. Posterous was recomended a day ago by a friend - the problem with it, or rather the problems: it's way too cute, as tumblr is oriented for multimedia and reposting (which is quite some overhead for what I have) and worst of all - my friend told me it'd derived from tumblr. And tumblr already messed the scheduled posts real bad, and the last two times were less than a month apart. I'm actually scared of tumblr software as this blog is not a full time job and it wasn't intended so.

Hehehe, ah, from a programming perspective it is quite easy and as Juan insists python is quite a nice approach. It should take a markup UTF8 encoded text file, parse the markup into HTML4 or whatever, slap a header with custom meta tags, include only the relevant part of a larger CSS (I do not edit the posts so the blog is as static as it can be), do some fancy modifications like set the title based on the first row contents of the source text file. Than, all this should be stamped with a date, a priority level (single digit) and some linking information (like if it is a part of a serie, than keep in line and don't break up). All these three stamps should be internal and never published. Than, when a post changes the priority level it should be put according to its receiving date (chronological order) on the same level as others, but without breaking a serie. That would make the perfect queue manager. Once every 24 hours another post is made available (published) and linked on the first page, actually the whole index gets regenerated - say if the decision is for 6 posts on a page, than every day the 6th post becomes the 7th and from the last entry on page 1 it becomes the first entry on page 2. Than there's a need for a schematic input interface, and a flexible (drag and drop?) queue interface.

Guess nobody made something that simple as most people into programming are up to regenerate the future Microsoft Word, but using a more obscure library than the other teams. For me that still implies a hosting service somewhere in the cloud, the evolution thing is null for the simple reason that I don't have a desktop 24/7 online, but a laptop and travel a lot meaning quite a few days in a row without getting online.

---

### Post by _outlawed_ on 2010-11-02
> **The Real Dave said:**
> I use and love Wordpress on Wordpress.com free hosting

The only problem is that they don't allow you to have any sort of advertising like Adsense, in case you wanted to make a little money from your blog.

---

### Post by The Real Dave on 2010-11-02
> **siddartha said:**
> Yea, queue management is the reason for a few plugins, markup is also a posibility once you have the plugins, yet the wordpress.com does not allow that. And I have no idea how to get a customised wordpress up and running on a free service that works (I already have tumblr for that - it does not work and has often problems with the post queue).


Get yourself over to 000webhost.com to get some free webspace, and then follow the Wordpress [5minute installer]("http://codex.wordpress.org/Installing_WordPress"). I've used 000webhost for the best part of a year (not for my blog mind you) and love them, considering it's free, it's a brilliant offer.

> **_outlawed_ said:**
> The only problem is that they don't allow you to have any sort of advertising like Adsense, in case you wanted to make a little money from your blog.

Personally I think that's a bit cheeky, getting free hosting from Wordpress.com, then loading your page with ads. Pay for your hosting, or host externally (000webhost.com being my recommendation), and then have all the ads you want.

---

### Post by Quadunit404 on 2010-11-02
Personally I prefer [0000free]("http://0000free.com/index.html") for my hosting. I have a site set up with them and I'm loving it.

---

### Post by _outlawed_ on 2010-11-02
> **The Real Dave said:**
> Personally I think that's a bit cheeky, getting free hosting from Wordpress.com, then loading your page with ads.

I wasn't meaning slamming ads all over your blog, I meant like 1 ad somewhere (like in the sidebar), not these idiots who have a blog and have their individual posts surrounded by 50 ads with another 50 inside the post itself thinking they are going to become millionaires.

---

### Post by The Real Dave on 2010-11-03
> **_outlawed_ said:**
> I wasn't meaning slamming ads all over your blog, I meant like 1 ad somewhere (like in the sidebar), not these idiots who have a blog and have their individual posts surrounded by 50 ads with another 50 inside the post itself thinking they are going to become millionaires.

I can see where you're coming from, but personally, I'm an [Ad-Free Blog]("http://www.adfreeblog.org/") kind of a guy ;)

---

### Post by Quadunit404 on 2010-11-03
Ads, while they can be useful for picking up some spare cash to cover your hosting costs, are a great way of delivering viruses (and by that I mean great for the criminal and bad for the user.)

Which is why I prefer ad-free as well. I'd rather not risk my visitors a virus infection over cover the costs of hosting (especially since my host is free **and** very good.)

---

### Post by bompus on 2010-11-23
Most of the free blog platforms out there will allow you to revenue share with them now. I personally use one called [blogReaction]("http://blogreaction.com/") that works well for me. Most of the bigger platforms that allow revenue sharing also use big ad networks like Adsense or Kontera, which filter out all of the issues with malware by serving up the ads themselves. Apart from a hosted solutions, Wordpress or Typepad wouldn't be bad although WP is getting kind of bloated recently.

---

### Post by joepie91 on 2010-11-23
As for the hosting, you could just grab a Byethost plan ([www.byethost.com](www.byethost.com)) which is free, and a free uni.cc domain. Combine those two (you can actually use DNS for that) and you have some space that's nearly identical to the average paid hosting plan.

As for the blog software... if you really need something simple, and you have a bit of time, you could try to learn PHP on w3schools.com in case you don't know it yet (will take about 45 minutes) and write something yourself. It really isn't hard. I can't really recommend any premade software as I haven't ever had to schedule posts.

---

### Post by siddartha on 2010-11-24
Thank you Joe for your reply.

Sadly I don't have time for that and I have already chosen wordpress. As crippled and bloated with eye candy it can be it has the advantage of being open both in the sense of the source and in the sense that I can export my database and do something with it (being a popular platform also means the export would be a popular format and I won't be stuck with moving by hand each post and comment later on).

This seems to be the main problem with open source projects. Besides the few who get waved a lot by talibans all other open source projects are redundant, quite pointless (they do not strive to solve a problem, but rather to copy or tweak a particular function) and no way willing to learn new tricks. As for going my way I've seen quite a few projects in this range and that means having a buggy half-baked overnight hack stuck in development limbo. I'd rather go for the lesser evil.

---

### Post by rajeev1204 on 2010-11-24
> **siddartha said:**
> Thank you Joe for your reply.

Sadly I don't have time for that and I have already chosen wordpress. As crippled and bloated with eye candy it can be it has the advantage of being open both in the sense of the source and in the sense that I can export my database and do something with it (being a popular platform also means the export would be a popular format and I won't be stuck with moving by hand each post and comment later on).

This seems to be the main problem with open source projects. Besides the few who get waved a lot by talibans all other open source projects are redundant, quite pointless (they do not strive to solve a problem, but rather to copy or tweak a particular function) and no way willing to learn new tricks. As for going my way I've seen quite a few projects in this range and that means having a buggy half-baked overnight hack stuck in development limbo. I'd rather go for the lesser evil.

..........................

---

