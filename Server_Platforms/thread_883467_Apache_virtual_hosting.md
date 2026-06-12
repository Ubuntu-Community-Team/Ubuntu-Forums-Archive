---
title: "Apache virtual hosting"
date: 2008-08-08
forum: Server Platforms
---

### Post by chrisab508 on 2008-08-08
Hey guys,
I have a server that's currently using hardy.  I have dhcp through my ISP and have set up an dynamic dns (dyndns.org) account.  I have a blog, some message boards, along with an online mail client for my mail server all running from the same server.  I wanted to setup virtual hosting for a few of those but had a few questions.  Take my domain name for example: example.dyndns.org;  if I wanted to use virtual hosting to setup a separate address for my forums, can I setup something along the lines of: forums.example.dyndns.org ?  Or would I want to register another dynamic dns hostname (forums.dyndns.org) and have that point my forums on my server?  I've been reading up about virtual hosting but was not able to find the answer to that question.  In all the configuration files, you need to specify another domain for the virtual host.  I assume that these other domains are domains that you need to purchase?  I've never had a domain that wasn't dynamic dns, so I'm not quite sure how to relate everything.  Another example, if I had the domain [www.example.com](www.example.com), would a virtual host just be another random domain name that points to the same server? i.e. wwww.example1.com but it really goes to [www.example.com/forums](www.example.com/forums) ?  or is something along the lines of forums.example.com ?

Sorry if this doesn't make too much sense,  I look forward to your help!


- Chris

---

### Post by windependence on 2008-08-08
Doing virtual hosting on a dynamic IP is kinda like fixing a car with chewing gum and wire, it might work, but it won't be pretty. You should see if you ISP offers you a static IP if it all possible. You may need a business account or if you don't mind, change ISPs. Mine only charges $4.95 a month for the static IP but others are more.

As to your other questions, if you own more than one domain, you would point your other domains at the same IP adrress or dynamic domain. So, all your domains would point to the same IP which is the IP of your server, and Apache takes care of figuring out shich domain is requesting what from the different document roots.

Someting like forums.example.com is another animal, it's a sub domain of example.com whereas a virtual domain is a completely different domain altogether.

-Tim

---

### Post by chrisab508 on 2008-08-08
Tim, thanks a lot for your response, you've clarified a few things, but I have one followup question:  What's the difference between owning multiple domains (and using different document roots for each) versus using virtual hosting/domains?  Now that you've explained subdomains, that clarifies that (at first i thought that forums.example.com was virtual hosting/domain, but you've made it clear that it isn't).

thanks,

- Chris

---

### Post by windependence on 2008-08-08
Well, using different document roots for each site IS virtual hosting. basically, virtual hosting just means that you are using one Apache instance to serve many domains. You can do this by using different IPs for each domain (IP based virtual hosting) or just by using one IP and having Apache figure out what domain made the request to the server and where to send it (name based virtual hosting). 

If you are using dedicated hosting, you would have an instance of Apache for each and every domain, and probably a unique IP address for each also.

More info here:

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

Hope this explains it more for you.

-Tim

---

### Post by chrisab508 on 2008-08-08
Thanks again Tim,
Alright, I think I understand.  So if my dynamic dns domain is: example.dyndns.org and I have forums (at example.dyndns.org/forums) as well as a blog (at example.dyndns.org/blog); then if I bought two domains: [www.my-forums.com](www.my-forums.com) (and pointed it toward example.dyndns.org/forums) and then [www.my-blog.com](www.my-blog.com) (and pointed it toward example.dyndns.org/blog) then this is essential virtual hosting?  Just not using apache to do it?  My question is, what's the need for using apache's virtual hosting feature if you're able to do it this way?  Do I not need to buy domain names if I use apache's virtual host feature?

Thanks,

- Chris

---

### Post by windependence on 2008-08-08
No, you can't just point it at your server because it won't magically know which document root to use for each domain. This is where Apache comes in. It knows from the packets where the requests come from (which site) and where to send the requests back to. If you point two doamins at the same server without using the virtual hosting feature in Apache, you will just get the same content on both sites.

-Tim

---

### Post by MJN on 2008-08-08
> **windependence said:**
> Doing virtual hosting on a dynamic IP is kinda like fixing a car with chewing gum and wire, it might work, but it won't be pretty.

If I may be so bold this is complete and utter nonsense.

There is nothing 'non-pretty' about using dynamic DNS with low TTLs. It works, and it works well.  I, like countless others, have never had any problems with it whatsoever.

Please stop spreading this FUD.

Mathew

---

### Post by windependence on 2008-08-08
No, I won't. It is not a great and wonderful way to do it.

Furthermore, from personal experience with my own production sites, when I started hosting my own sites a few years ago, users e-mailed me and called me to inform me that they could not reach the site. This was traced back to the fact that since my traffic was redirected, their companies were specifically blocking my sites. It is a FACT that they are losing page views and potential web traffic doing it this way. The CORRECT way to host is with a static IP. 

I'll remind you this is the SERVER forum, and as such, people may actually be wanting to run enterprise class sites and make money. because something SEEMS to work for you doesn't mean it works for everyone.

If you have a problem with what I post, please report it to the moderators, I would be happy to respond to the complaint.

-Tim

---

### Post by MJN on 2008-08-08
Just as I thought - no technical substance. Your talk of 'redirecting traffic' suggests you don't actually know what dynamic DNS is at all (hint: it has nothing to do with redirection whatsoever).

Read the OP again - does it sound like an Enterprise setup to you?

Sure, make people aware of the pros and cons of alternatives, but please don't liken dynamic DNS to 'fixing a car with chewing gum and wire' as it is very misleading at best.

Mathew

---

### Post by windependence on 2008-08-08
This is why Ubuntu server is not seen in business as on the same level as CentOS, RedHAT, and SuSE. Everyone wants to kludge things together just so they "work" and no one wants to do the things the correct way. You might notice I only frequent the server forum. There is a reason for this. I would like to see Ubuntu's server product become respected as the others are. This will not happen advocating dynamic DNS and software RAID.

And what is with the no technical substance comment. I run a site today with 13,000 page views per day and 5 million hits per month. This would never have happened on dyndns.

-Tim

---

### Post by MJN on 2008-08-08
You're drifting off the point so perhaps we are best agreeing to disagree. I meant there was no technical substance supporting your argument, not of you personally.

To the OP, my apologies for this temporary diversion but there is no reason why you will have to fork out $5/month to do what you want to do. Dynamic DNS is perfectly fine for your needs and to suggest otherwise is a red herring to the questions you have asked. Static IP addresses have absolutely no bearing on the matter.

Mathew

---

### Post by chrisab508 on 2008-08-08
> No, you can't just point it at your server because it won't magically know which document root to use for each domain. 

Then why do I have my dyndns domain going to my blog (example.dyndns.org), and my .tk domain going to my forums (example.dyndns.org/forums) and both redirect to the correct sites?

Also, thank you for all the replies, I don't really mind the back and forth banter, I enjoy seeing two sides to an arguement :)

---

### Post by MJN on 2008-08-08
> **chrisab508 said:**
> Then why do I have my dyndns domain going to my blog (example.dyndns.org), and my .tk domain going to my forums (example.dyndns.org/forums) and both redirect to the correct sites?

Read the sentence that you snipped off the end! ('That's where Apache comes in')

Apache examines the HOST header sent by the client and hence is able to serve up the correct pages despite both requests coming on the same IP address.

> Also, thank you for all the replies, I don't really mind the back and forth banter, I enjoy seeing two sides to an arguement :)Debate is indeed healthy and I know Tim gives as good as he gets!

Mathew

---

### Post by kihjin on 2008-08-08
I personally would prefer to host off of a static ip in the long run, but a get-it-done quick strategy using a dynamic ip is not much different than a load balancing system. Keep your TTL at 300s and you'll be fine. Some people might have trouble getting to the site within that 300s, but depending on how frequently your IP actually changes, it may be a moot point.

As for virtual hosting, say you have two domains, each domain needs two subdomains.

[www.example.com](www.example.com)
[www.mysite.com](www.mysite.com)

When a client connects to your machine's port 80, it will typically be sending a HTTP/1.1 request. Amajor difference between 1.1 and 1.0 is the addition of the Host: field in the request. It is up to the visitor's browser to send this field to the server it is connecting to. In the case of example.com, the Host field will be set to example.com.

Apache uses this field to determine which virtual host (and thus from which directory) to server content from. This is done with the ServerName and ServerAlias directives. You could do

ServerName example.com
ServerAlias *.example.com

This should allow [http://*.example.com](http://*.example.com) in addition to [http://example.com](http://example.com) to be served by apache for the document root you specify in your virtual host block.

Subdomains are another ball of worms, as one poster pointed out. If you are comfortable with static subdomains, you only need to add another virtual host to your configuration file with the ServerName set to the subdomain you want to serve.

For me, this would be a hassle since hosting clients want to be able to create subdomains on the fly. What I've got setup is a system where clients may simply create a directory in a specific location under their domain root. This is automatically (no restart) handled by apache once the directory gets created.

---

### Post by chrisab508 on 2008-08-08
Once again, thank you for your replies; there is just one ambiguity that I'm trying to sort out:

> Read the sentence that you snipped off the end! ('That's where Apache comes in')

Apache examines the HOST header sent by the client and hence is able to serve up the correct pages despite both requests coming on the same IP address.


That's all good, except what's the difference between using virtual hosts (i.e. using the virtual host tags in httpd.conf) versus what  I described (i.e. having different domain names redirect to different folders) ?  As I described, I have my dyndns direct to a blog, whereas I have my .tk domain direct to dyndns/forums.  I'm not using any of the apache virtual host configurations (i.e. in httpd.conf) or anything of the sort.  So what's the difference between doing it my way, and using the virtual host tags?

Sorry for my ignorance, I've just started doing work on a server this summer and I'm very intrigued

---

### Post by MJN on 2008-08-08
It sounds like you are using virtual hosting, but perhaps not realising!

You really need to tell us the URLs you're hosting, then we can see if they point to the same IP address. If they do, then post your config and you will likely find you were one step ahead and using it all along...

(the alternative, which I'm sure Tim and I would both agree is rather poor, is that one of your domains has a 'layer 7' redirect in place i.e. another web server redirects the client to your other domain but with a different path)

Mathew

---

### Post by kihjin on 2008-08-08
Virtual host "redirection" through apache is an internal process and is transparent to the visitor. 

What you're describing sounds like an external redirection, although I can't comment on whether it is on par with apache's internal redirection since I'm not too familiar with dyndns' service software. 

The difference has to do with user experience. In one case the user sees the URL as a subdomain, in the other case he sees it as a folder under a domain.

[edit]
@MJN Aha! 'layer 7' redirect, I was wondering if there was a term for this sort of service...

---

### Post by chrisab508 on 2008-08-08
Alright, makes sense now, I believe what I'm using is the layer 7 redirect.  I'm not actually "using" it, I just set it up to see if what I was thinking about would actually work.  My blog is *** and the forums (which are somewhat of a joke between my brother and I, so don't judge) are **** I have nothing in my apache configuration files that is using virtual hosting.

---

### Post by kihjin on 2008-08-08
I just visited [http://www.jediforums.tk/](http://www.jediforums.tk/)

Looks like it's a frame based redirection. This keeps the URL from changing. If you've got firefox you can right-click and select "This Frame->" to get more information about it.

---

### Post by MJN on 2008-08-08
Yes, I'm afraid so.

There are a number of drawbacks with having such a redirect in place, particular in this manner i.e. the use of a frame 'wrapper' around your forum site means that search engines may have limited success in trawling your site and, furthermore, some web browsers may struggle too - particular those on fringe platforms like mobiles/PDAs. You can also face problems trying to make an external reference to a URL on your site as there are many cases where a frameset wrapper would simply not work.

I strongly recommend moving on with investigating true virtual hosting on Apache - it really is quite straightforward (once you know how of course!) and will give you maximum flexibility for the future.

Mathew

---

### Post by chrisab508 on 2008-08-08
Alright, so the .tk domain just creates a new frame, which in turn loads my original URL?  So is there a way that you would use .tk domains with proper virtual hosting?  I'm not trying to use virtual hosting (because this frame based redirect seems to work fine for me) I'm just trying to understand how it really works, and how it would be done by a seasoned veteran

---

### Post by MJN on 2008-08-08
You'd just point the DNS (A record) for [www.jediforums.tk](www.jediforums.tk) at your IP address (just like you have done for burgner2.dyndns.org) and Apache will examine the HOST header request of connecting clients and serve up the relevant site/pages. It does this through each 'virtual host' being uniquely identified by a ServerName ... directive.

Mathew

---

### Post by chrisab508 on 2008-08-08
Alright, after this long discussion, I finally understand the difference between the two scenarios I gave, as well as when you would use virtual hosting through apache.  Thanks a lot for the help guys!

- Chris

---

