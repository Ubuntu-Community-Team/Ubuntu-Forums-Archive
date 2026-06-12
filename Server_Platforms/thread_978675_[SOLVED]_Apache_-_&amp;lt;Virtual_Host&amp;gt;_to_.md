---
title: "[SOLVED] Apache - &amp;lt;Virtual Host&amp;gt; to a link"
date: 2008-11-11
forum: Server Platforms
---

### Post by victorbrca on 2008-11-11
Hi all,

  Does anyone knows if there's a way to link the section <Virtual Host> to a link?

  I will be moving my blog into my site, but I'm using Joomla. Everything is in the same root directory and there's no root for the blog, just a link.

Example:
> Site: [http://www.my-url.com/](http://www.my-url.com/)
Blog: [http://www.my-url.com/index.php?option=com_content&view=section&layout=blog&id=5&Itemid=53](http://www.my-url.com/index.php?option=com_content&view=section&layout=blog&id=5&Itemid=53)


Thanks!!

Vic.

---

### Post by oneloveamaru on 2008-11-11
Link Virtual Host to a link? I'm confused dude. A virtual host is just telling apache that site is located on the server. If you want it to go somewhere else you do a redirect. A redirect will send it anywhere you want... to another website, etc.

Everything is in the same root directory and there's no root for the blog... WHAT?  If everything is in the same root directory how is there not a root for the blog?

In Apache, if you have a virtual host setup, we will call it [www.site.com](www.site.com), with the root pointed to say... /srv/www/site...   so when you access [www.site.com](www.site.com) anything in that folder comes up, as long as you have the virtual host set up correctly. If you create a /srv/www/site/blog and throw your blog stuff in there, you don't need to make anymore changes to the virtual host config. you just access that with [www.site.com/blog](www.site.com/blog)

Now if you want it to be blog.site.com then you need to create a new virtual host and if you wanted [www.site.com/blog](www.site.com/blog) to redirect to blog.site.com then you would need to redirect or a rewrite. I would do a 301 redirect to make it search engine friendly.

Explain this out much more dude. You can do lots of things with Apache, I'm just not sure exactly what you are asking. Maybe I answered it already?

---

### Post by victorbrca on 2008-11-11
Hey dude, thanks for the reply. 

As I mentioned before, I'm using Joomla for my site. The blog is not a separate site, but an embedded link within Joomla (a module). 

Take this as an example:

> Main site info:
URL: [http://www.my-url.com/](http://www.my-url.com/)
root: /var/www/site1
alias: [http://www.my-url.com/](http://www.my-url.com/)

Blog 
URL: [http://www.my-url.com/index.php?opti...id=5&Itemid=53](http://www.my-url.com/index.php?opti...id=5&Itemid=53)
root: N/A
alias: [http://www.my-url.blog.com/](http://www.my-url.blog.com/)

Here are two screenshots to help a bit more:


**Main site**
[IMG]http://wazem.dyndns.org/temp/ubuntu-forum/blog/main.png[/IMG]



**Blog**
[IMG]http://wazem.dyndns.org/temp/ubuntu-forum/blog/blog.png[/IMG]

---

### Post by oneloveamaru on 2008-11-11
A picture is worth a thousand words!

OK, so you want to make [http://www.my-url.com/index.php?opti...id=5&Itemid=53](http://www.my-url.com/index.php?opti...id=5&Itemid=53) appear as [http://www.my-url.blog.com/](http://www.my-url.blog.com/)  ??

Have you tried this? [http://extensions.joomla.org/component/option,com_mtree/task,viewlink/link_id,1617/Itemid,35/](http://extensions.joomla.org/component/option,com_mtree/task,viewlink/link_id,1617/Itemid,35/)

---

### Post by victorbrca on 2008-11-11
Awesome... I'll have a look at that add-on and see if it will apply!! 

Thanks a lot!! :)

Vic.

---

