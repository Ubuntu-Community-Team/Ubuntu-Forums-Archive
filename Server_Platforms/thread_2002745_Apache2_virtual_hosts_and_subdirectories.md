---
title: "Apache2 virtual hosts and subdirectories"
date: 2012-06-13
forum: Server Platforms
---

### Post by fernandoch on 2012-06-13
Hello,

I have a domain example.com in a virtual host and working properly. 

```
<VirtualHost *:80>
DocumentRoot /www/example
ServerName www.example.com

# Other directives here

</VirtualHost>
```

I want to add a wiki in example.com/wiki and I would like to have it in a virtual host. 

Can that be done? If yes, then how?

Thank you.

---

### Post by volkswagner on 2012-06-13
You certainly can add the wiki to a sub directory.  You won't even need a separate vhost file since the wiki would be available using domain.com/wiki in the url.

If you wanted a vhost file you may be interested in setting up a sub domain to access the wiki, such as wiki.domain.com.

You would create the vhost file to look like:

```
<VirtualHost *:80>
DocumentRoot /www/example/wiki
ServerName wiki.example.com

# Other directives here

</VirtualHost>
```

Then:

```
sudo a2ensite wiki
```

```
sudo service apache2 reload
```

---

### Post by fernandoch on 2012-06-13
Thank you for the reply.

Sure I can add it to a subdirectory, but then I would mix the logs with the main server. I would like to have the logs separated as well as to have more control with a virtual host.

The other approach you are giving me is not recommended by mediawiki

[http://www.mediawiki.org/wiki/Manual:Short_URL#Defaults](http://www.mediawiki.org/wiki/Manual:Short_URL#Defaults)

Check the last URL, the same as the one you suggested.

Any other advices?

---

### Post by spynappels on 2012-06-13
From the MediaWiki site:


	> Warning: this method may create an unstable URL structure and leave some page names unusable on your wiki. See Manual:Wiki in site root directory. Please see the article Cool URIs don't change and take a few minutes to devise a stable URL structure for your web site before hopping willy-nilly into rewrites into the URL root.

So your site may not be affected, but if it is, you'll need to use the example.com/wiki/page structure and parse out the logs manually.

---

### Post by fernandoch on 2012-06-13
So in conclusion there is no way to create a virtual host for a subdirectory?

---

### Post by volkswagner on 2012-06-13
I'm no expert, but I fail to see the technical difference between [www.example.com/wiki/Article_title](www.example.com/wiki/Article_title) and wiki.example.com/wiki/Article_title.

I don't see how using a subdomain will cause an issue.  If you want a separate vhost, and don't want to purchase a second domain name, this is really your only solution.

Is this just an issue when using short urls?  Would eliminating the short url be a show stopper?

---

### Post by spynappels on 2012-06-13
Well, there is as volkswagner has said, it is just that in this case it may not work as well as expected. You could try it and see if the undesired behaviour manifests itself, it could be that what you are trying to set up does not have the problems MediaWiki warns of.

If it does, then you'll just have to do it the recommended way.

---

### Post by fernandoch on 2012-06-13
> **volkswagner said:**
> I'm no expert, but I fail to see the technical difference between [www.example.com/wiki/Article_title](www.example.com/wiki/Article_title) and wiki.example.com/wiki/Article_title.

I don't see how using a subdomain will cause an issue.  If you want a separate vhost, and don't want to purchase a second domain name, this is really your only solution.

Well me too, but this is what they are recommending. 

> **volkswagner said:**
> Is this just an issue when using short urls?  Would eliminating the short url be a show stopper?

Of course, with the competition we have around, you have to try to optimize everything, even URLs.

---

### Post by fernandoch on 2012-06-13
> **spynappels said:**
> Well, there is as volkswagner has said, it is just that in this case it may not work as well as expected. You could try it and see if the undesired behaviour manifests itself, it could be that what you are trying to set up does not have the problems MediaWiki warns of.

If it does, then you'll just have to do it the recommended way.

Well, maybe when installing extensions or any other addons, I could face problems with a subdomain. This is why I was asking the question in here.

And we cannot afford having google parse wrong URLs, then modifying them because of problems... So we have to be sure from the beginning.

---

