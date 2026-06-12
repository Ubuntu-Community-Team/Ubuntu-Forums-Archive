---
title: "Site www prefix not working"
date: 2012-09-03
forum: Server Platforms
---

### Post by Delarth on 2012-09-03
I am running Ubuntu Server 12.04 x64-bit and currently I have run into a bit of a snag with my internal site. I can access the site when I go to [http://mysite.internal](http://mysite.internal) however when I try going to [http://www.mysite.internal](http://www.mysite.internal) it brings up a page that just says 
**Index of /**

 [IMG]http://www.orion.int/icons/blank.gif[/IMG]NameLast modifiedSizeDescription

The default It Works! apache index page loads without the www. Do I need to change something in the DNS records? Currently my DNS has these records:
```

@       IN      NS      localhost.
@       IN      A       192.168.1.102
@       IN      AAAA    ::1
ns      IN      A       192.168.1.102
www     IN      A       192.168.1.102
```


I also saw some places mention adding a second ServerAlias under the apache files for the site however that doesn't seem to have worked either.

---

### Post by Doug S on 2012-09-03
I don't think your issue is with your DNS records.
I think your issue might be with your /etc/apache2/sites-available/default file.
Is that file unchanged from the installation?
Is the first line:```
<VirtualHost *:80>
```

---

### Post by SeijiSensei on 2012-09-04
In the <VirtualHost> container, you need

```

ServerName  www.example.com
ServerAlias example.com

```

This assumes you're using [name-based virtual hosting]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").

---

### Post by Delarth on 2012-09-04
The first line is
```
<VirtualHost *:80>
```and I do have 
```
ServerName www.example.com
ServerAlias example.com
```inside the virtualhost container


The entire sites-available file looks like this:
```
<VirtualHost *:80>
        ServerAdmin webmaster@site.internal
        ServerName www.site.internal
        ServerAlias site.internal *.site.internal
        DocumentRoot /srv/www/site.internal/public_html/
        ErrorLog /srv/www/site.internal/logs/error.log
</VirtualHost>
```

---

### Post by Doug S on 2012-09-04
I don't have any "Servername" or "ServerAlias" lines, and my internal stuff works fine for both www prefix and not. Perhaps try that, for a test.
 
Going back to your DNS records, maybe post the results for either "dig" or "nslookup" for both [www.mysite.internal]("http://www.mysite.internal") and mysite.internal. Is it mysite or site? And maybe post your entire db.mysite file instead of just a portion. Myself, for this line:```
@       IN      NS      localhost.
```I would have done this:```
@       IN      NS      ns.mysite.internal.

```But if I understand correctly, you are actually accessing the server when you use [www.mysite.internal]("http://www.mysite.internal"), so I don't know that it matters.

---

### Post by Delarth on 2012-09-04
Well it seems to be working now. Commenting out the ServerName and ServerAlias has made everything work. I never thought about removing those two since pretty much every guide out there tells you to include them.
As for changing that line you mentioned Doug, I had done that just never updated it in the post. I was just using site and mysite as replacements for the actual domain name.

---

### Post by Doug S on 2012-09-04
The [Ubuntu server guide ]("https://help.ubuntu.com/12.04/serverguide/httpd.html")lists the use of ServerName as optional...
I suspect there is still a mystery here, because what Seiji said should have worked. I have never done it, because I never had to. For a test, I added ServerName and ServerAlias lines, and access with or without the www URL prefix still worked fine.
 
Anyway, glad you got it working.

---

### Post by SeijiSensei on 2012-09-04
You also need to have the "NameVirtualHost *:80" directive activated, though I'm pretty sure that's the default with Ubuntu.  It's in /etc/apache2/ports.conf.

If you only use /etc/apache2/sites-available/default and make all your changes there, then the ServerName and ServerAlias directives do not matter.  The directives in that file apply to any URL that does not match a ServerName with named-based virtual hosting is active.

Try browsing to http://ip.of.your.server/ instead of a symbolic name.  Do you get the same pages as with the hostname-based URLs?

---

### Post by Delarth on 2012-09-05
Double checked and the NameVirtualHost *:80 is activated in ports.conf
When I replace the symbolic name with the local ip I get the same pages.
I do want to thank both of you for helping with everything.

Of course there is now something strange going on. I have a laptop I setup as a sort of test server where I make changes and then copy them over to the main server. Well once they both started resolving with the www I stopped making any changes. Last night I turned off my test server and my desktop but left my main server running.

When I got up this morning attempting to access the site on the main server with www resulted in it not working :mad: but I can still access it without using the www. I turned on my test server/laptop and tried to navigate to the test domain and using www worked just fine. Keep in mind that the files are identical between both of these servers.

What strikes me as most interesting is when I try to navigate to the main site using www I get the following error from my browser:
> Firefox can't find the server at [www.mysite.internal]("http://www.mysite.internal").That period at the end of internal makes me thing there might be a typo somewhere but I looked over all the bind files and couldn't find one, I even compared them to the test files and things were identical, aside the name of the site and the IP address of course.



EDIT: Now for some reason when I use the www it resolves just fine again. I have no clue where the issue could be coming from at this point and I know its not just my desktop because I tried accessing the site from my cellphone and another computer in the house and they all responded the same, even after clearing out the cache on the browsers.

---

### Post by SeijiSensei on 2012-09-05
> **Delarth said:**
> Double checked and the NameVirtualHost *:80 is activated in ports.conf
When I replace the symbolic name with the local ip I get the same pages.

Then it's not really paying any attention to the server names and just giving you the site defined in /etc/apache2/sites-available/default regardless of the requested URL.  If you are only hosting one site, that is a perfectly fine solution.

---

