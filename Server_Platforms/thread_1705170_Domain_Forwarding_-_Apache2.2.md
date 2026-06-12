---
title: "Domain Forwarding - Apache2.2"
date: 2011-03-11
forum: Server Platforms
---

### Post by ktz84 on 2011-03-11
I have started selling through ebay and bought a domain. I have forwarded the domain to my a free computer which I have which I am running ubuntu and apache2.2. I have it set the name servers up to point to my webserver, which also hosts my own personal website, so using virtual host declarations to redirect traffic to the correct sites, and that's all working fine. However my new domain (same name as my ebay name - view to moving away from ebay eventually) points to a basic web page which I setup simply saying under construction however it's going to be quite a while under construction so now I want to redirect all traffic coming to the [www.domainname.com]("http://www.domainname.com") or domainname.com to my ebay listings however I still need to be able to access [www.domain.com/SomeTestSite]("http://www.domain.com/SomeTestSite") or domain.com/SomeTestSite so that I can continue to test different things from remote locations. This is why a redirect from my domain host will not work as it will not allow me to access my test apps.

I'm unsure how to do achieve this.

Any help appreciated. I'm good at following guides but not so hot when I have to think for myself but any help is appreciated.

Thanks

---

### Post by volkswagner on 2011-03-11
Why not just add a nice large text or picture link on your construction page, and point that to your ebay listing.  This will also help build SEO, which a redirect will not, unless it were permanent redirect.  I don't think you want a permanent redirect since you will be adding content to this domain eventually.

Really first think if you actually want a redirect, if this site will eventually take real visitors in the near or distant future.

---

### Post by ktz84 on 2011-03-11
I've taken on rather a lot in that I'm at present teaching myself book keeping & taxation, all in an effort to keep costs to a minimum even though the business is profitable from the get go but my time is limited as I have normal 9-5 job as it doesn't have the volume yet to support me and my partner which is why I'm trying to keep costs to the minimum.

I have a copy of zen cart which I'm testing however I just don't have the time at the min to learn what is needed to get the most out of it as I'm concentrating on getting my recording keeping sorted (phreebooks or sage 50 - one free but very limited information on at the min and the other very expensive but with a very wide user base (in the UK where I'm based)  hence why I'm keeping other costs under control).

My guess is tha the website will take at least 6 months but more likely a year to sort.

Is that long term?

I'd thought of a basic webpage consisting of logo, some info about the products we sell and a link to ebay but I was actually worried that I might hurt my SEO by my lack of content. Is that likely with the timescales I'm talking about?

---

### Post by volkswagner on 2011-03-11
Well, the way I see it is a couple choices.

I just don't see how you can do a proper redirect, and maintain a test site.  You may want to consider the link on main page, or use a subdomain for your ZenCart, such as shop.domain.com.

Sorry, I just can't think of a more elegant solution.

Otherwise you could do a separate test server and just edit the host file on the local machine or LAN connected machines, to point to the local test server.  This obviously would not work from remote locations (over Internet) as in your original post.

---

### Post by SeijiSensei on 2011-03-11
> **ktz84 said:**
> I want to redirect all traffic coming to the [www.domainname.com]("http://www.domainname.com") or domainname.com to my ebay listings however I still need to be able to access [www.domain.com/SomeTestSite]("http://www.domain.com/SomeTestSite") or domain.com/SomeTestSite so that I can continue to test different things from remote locations. This is why a redirect from my domain host will not work as it will not allow me to access my test apps.

In Apache, you can do this with Rewrite rules and Aliasing.  Rewrite the URL "^/$" to "http://www.ebay.com/whatever" then alias /SomeTestSite to /path/to/testsite like this:

```

RewriteEngine     on
RewriteRule       ^/$  http://www.ebay.com/mystore/  [R]
Alias             /SomeTestSite  /path/to/testsite
<Directory "/path/to/testsite">
    whatever
</Directory>

```

Incoming requests for [http://www.example.com/](http://www.example.com/) will match the regular expression "^/$" and be rewritten to the ebay URL.  The [R] switch forces a subsequent redirect. Requests for [http://www.example.com/SomeTestSite/](http://www.example.com/SomeTestSite/) will be handled by the alias and served by files in /path/to/testsite.  You need either a <Directory "/path/to/testsite"> or a <Location "/SomeTestSite"> directive defining access to the published directory.

You can massage URLs pretty much any way you'd like using [mod_rewrite]("http://httpd.apache.org/docs/current/rewrite/").  You might want to browse the [Guide]("http://httpd.apache.org/docs/current/rewrite/rewrite_guide.html") which has many examples. This is an extremely simple use of URL rewriting compared to what you'll find there.  

To use mod_rewrite, you'll need to learn the basics of [regular expressions]("http://www.grymoire.com/Unix/Regular.html"), but that's a valuable skill to have. The example above "^/$" consists of the anchor "^" denoting the beginning of the string, the slash which defines the base URL, and the "$" delimiter that represents the end of the string.  Thus "^/$" matches "/" and only "/".  Any other URL is processed normally.

---

### Post by ktz84 on 2011-03-12
Thanks SeijiSensei for that guide. I had noticed the rewrite rules in apache but must admit I was more than a little confused so I'll give your solution a shot and see how I get on.

---

### Post by ktz84 on 2011-04-27
[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") apologies for not getting back to say thanks for the advice. It is working perfectly.

---

