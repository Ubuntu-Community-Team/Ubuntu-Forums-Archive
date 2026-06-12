---
title: "website hijacking"
date: 2014-03-30
forum: Server Platforms
---

### Post by Drone4four on 2014-03-30
About a week ago I deployed my first digitalocean droplet.  I used 12.04 and installed Apache, MySQL and PHP. I successfully got my index.html to load in my browser when entering my droplet’s ip address indicated in my digitalocean control panel.  That same weekend in a humble state of accomplishment, I shared the ip address to my freshly deployed LAMP stack with a friend of mine from work who works in our IT department.  This is the same person who recommended digitalocean to me in the first place. He and I share a lot in common.  

I Googled a string of uniquely worded content from my site in quotation marks yesterday and discovered that someone had mirrored my HTML and CSS code onto their server with a domain name.  I did a whois query and discovered the domain registered to someone in Texas in December of 2013.   My site was live on someone else’s server before I had the opportunity to bind my ip address to the domain name I registered, which was something I was planning on doing this weekend. 

I didn’t want my content mirrored like this so I destroyed my droplet last night.  About an hour or two later this third party clone of my site indexed on Google went down too. 

What the hell could be going on here?

I have a suspicion.  I shared my digitalocean droplet ip address with only one person - - that co worker I mentioned earlier.  This coworker is a very gifted individual.  He has worked at fortune 500 companies in the past and is in the process of studying to write advanced level Cisco certifications.  The domain name which the third party used was goofy, goofy in a way that matches my coworker’s playful character.  I suspect it could be my co worker playing a prank on me, but I don’t know for sure.  

Is there any other logical explanation for someone getting a hold of my droplet’s ip address, hijacking my content and hosting on their own public server? Could this be a malicious third-party who somehow discovered my hexadecimal ip address and decided to copy my HTML? If this happens to other people, why would third-parties do such things? What could be his or her motive? Do they have something financial to gain?  Do these kinds of third-party hijackers do so for similar reasons that DNS squatters register potential names to sell to the highest bidder? Do they use it for hidden, malicious intent involving spam or malware or something? 

Is there any other possible explanation for this phenomenon I am experiencing?

---

### Post by TheFu on 2014-03-31
IPs are public. Searching the entire internet for stuff on port 80 takes less than 24 hours these days.

I've been on the internet since the 1990s and have seen my content stolen many times, usually by well meaning people who were afraid that it would disappear.  It usually just takes a nicely worded email to the webmaster to handle.

If you don't want people to use iframes with your content, then block that.  Check out YaCy to see what's possible.

I'd be concerned over putting anything based on PHP on the internet. I'm not the only one. [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet) is a group around creating best practices for web-app security. There is a local group in my metro area and I've spoken at a few others around the world. Nice folks.

Be extremely careful with PHP. E-X-T-R-E-M-E-L-Y.

---

### Post by Drone4four on 2014-03-31
Thank-you TheFu for your reply.

```
<meta name='robots' content='noindex,nofollow' />
```

If bind my ip address to a domain name and append the above code nested beneath my header tag, what will this do?  [According to Google support docs]("https://support.google.com/webmasters/answer/93710?hl=en"), it will prevent all robots from indexing the page on my site. But is it conceivable that the bots you speak of (the ones which scan the entire internet in 24 hours) still get a hold of the ip address binded to my domain?  Or should the code in my meta tag prevent that? I suppose I am just asking hypothetically here.  

Is it at all possible to keep my domain private and unlisted, so as to make it accessible only to the people who I directly give the address to?

I checked out YaCy.  I found the Wikipedia entry but [the actual homepage for the project]("http://www.yacy.net/") is offline right now.  To use the YaCy search engine, do I have to be a member of the peer-to-peer network and access it via my localhost:8090?

I don't intend on using PHP.  I am not a programmer. I just installed PHP for the sake of it.  But is there any danger having PHP installed on my server even though its mostly inactive? What if I install a service like WordPress which uses PHP?  Should I worry about PHP then?  If I were careless with PHP, what's the worst that could happen?

---

### Post by TheFu on 2014-03-31
> **Drone4four said:**
> Thank-you TheFu for your reply.

```
<meta name='robots' content='noindex,nofollow' />
```

If bind my ip address to a domain name and append the above code nested beneath my header tag, what will this do?  [According to Google support docs]("https://support.google.com/webmasters/answer/93710?hl=en"), it will prevent all robots from indexing the page on my site. But is it conceivable that the bots you speak of (the ones which scan the entire internet in 24 hours) still get a hold of the ip address binded to my domain?  Or should the code in my meta tag prevent that? I suppose I am just asking hypothetically here.  

Is it at all possible to keep my domain private and unlisted, so as to make it accessible only to the people who I directly give the address to?

I checked out YaCy.  I found the Wikipedia entry but [the actual homepage for the project]("http://www.yacy.net/") is offline right now.  To use the YaCy search engine, do I have to be a member of the peer-to-peer network and access it via my localhost:8090?

I don't intend on using PHP.  I am not a programmer. I just installed PHP for the sake of it.  But is there any danger having PHP installed on my server even though its mostly inactive? What if I install a service like WordPress which uses PHP?  Should I worry about PHP then?  If I were careless with PHP, what's the worst that could happen?

Servers can request all sorts of things from clients ---- which are completely ignored. robots.txt are ignored all the time.

The YaCy reference was just to show that anyone can run a webcrawler from anywhere in the world and find any website, running on any port.

No, you CANNOT prevent people from connecting to your URL unless you put in a highly restrictive firewall ... which sorta defeats the point of having a website on the internet.  So ... you can stop putting it on the internet and force only your friends to access it through a VPN, but that is usually more trouble than it is worth for a hobby.  OTOH, YOU might want a VPN so that when you are away, it is safe to remote in to the home network.  openvpn is the tool of choice for that or you can just use ssh like most UNIX folks do.

Should you worry about PHP. This is an opinion question - I think so. My CSO thinks so. Our corporate poilicy doesn't allow PHP on the internet. We can run it internally, only accessible over VPN, but we have to get a "variance" approved by a VP. It is easier to use perl, python, ruby, ... almost anything else ... except Java. That is prohibited here too since Oracle took over.  I don't think most java is nearly as bad as most php, but any code can be dangerous.  I think that wordpress, when run by professionals, is as secure as any other blog engine.  However, last month, I helped a guy here discover that his wordpress blog was hacked. He came here looking for help on web analytics that stopped working and left thinking his server had been hacked and we probably being used as C&C for a botnet.

Then internet isn't a friendly place for the server or network administrator. We need to be proactive, aggressive, protective.   BTW, backups are the #1 security tool - be certain you have those working perfectly and stored offline so you can compare against something when you are hacked. "when", not if. ;)

As to people copying your content - there are all sorts of ways to make it more difficult, but in the end, that doesn't work for a determined copier. If you put text and/or images on the web, they will be copied.  If you put them into non-easily found URLs, one of your friends will share that URL somewhere (probably inside gmail) and then google will start searching for it.  That happened to me.  If you don't want others to access the data, then don't let them see it or force only a VPN to have access.

---

### Post by SeijiSensei on 2014-04-01
I think you and your higher-ups are overly paranoid about PHP.  It's certainly a lot stronger since the Zend folks took over development.  Most problems with PHP sites have to do with bad programming practices, not inherent deficiencies in the language itself.  

OP, if there are no .php (or .ph*) pages on your site, then nothing will invoke the PHP engine.  

Instead of placing "nofollow,noindex" in a <meta> tag on each page, you can tell Apache to send these restrictions in advance of delivering the page content like this:
```

Header set "X-Robots-Tag" "noindex,nofollow"

```
To set this globally, add it to the bottom of /etc/apache2/apache2.conf right above the "IncludeOptional" directives.

---

### Post by Lars Noodén on 2014-04-01
I've used PHP in the past and am leery of its use.   I've come to see PHP as a last resort.

[http://me.veekun.com/blog/2012/04/09/php-a-fractal-of-bad-design/](http://me.veekun.com/blog/2012/04/09/php-a-fractal-of-bad-design/)

Unfortunately there are many things that, purely from a user perspective, are great but from a development or sysadmin perspective are a terrible nightmare.  

There are many sites that use PHP just to get standardized headers, footers and navigation menus.  If that is what you are looking to do, then you can do all that with [Server-Side Includes](http://httpd.apache.org/docs/current/howto/ssi.html) more securely.  Just be sure to use IncludesNOEXEC in the options, for extra protection.

About the copying, you can try complaining to the site's owner or to the organization where the ip number is registered.  About the meta tags, I'd use index rather than noindex because, usually, you want the honest search engines like YaCY and Google to find your page for people  The dishonest search engines will happily ignore both robots.txt and meta tags.  

A more obnoxious route would be to PGP sign the page's content and then, when it gets copied, come down with the DMCA or EUCD.  But I don't think highly of that option and the recommendation of a polite letter is good and may be enough to clear up the misunderstanding.

---

### Post by m-dw on 2014-04-01
> **Drone4four said:**
> Is it at all possible to keep my domain private and unlisted, so as to make it accessible only to the people who I directly give the address to?

No-one else mentioned it, but if you want your content to remain private you could always restrict access with password protection.  If you're really paranoid you should also protect it with SSL so that no-one can pick up the encoded username/password in the http request headers.

---

### Post by SeijiSensei on 2014-04-01
> **Lars Noodén said:**
> There are many sites that use PHP just to get standardized headers, footers and navigation menus.

All my sites contain dynamic content and rely on a database backend.  For that I need some type of programming environment; PHP works for me.

That article you cited raises a lot of tiny issues and points to problems that most of us never encounter.  Sure I don't like having to remember that the order of parameters in strstr() is different from that in preg_match(), but those are quibbles.  One of his security examples concerns a broken crypt() function.  Does anyone even use crypt for password hashing these days?  Certainly not me.  The section on debugging seems to criticize PHP for not offering functionality that is irrelevant to a scripting language.   His discussion of globals is entirely off-the-mark since he fails to acknowledge the existence of the $GLOBALS built-in array.  I could go on, but I've seen these kinds of rants from programmers, and they all fail to move me to switch languages.  

Now I've been writing sites like these for some 15 years now, so I'm probably better able to protect my code from potential dangers.  Still if you think about the security implications of what you are writing while you are writing it, I don't think PHP is per se less secure than competing languages for developing web applications.  I'll just observe that it is the language of choice for many large projects like WordPress and Joomla.

---

### Post by TheFu on 2014-04-01
The core PHP project has a history of releasing code that THEY KNEW contained major bugs in.  If the project really is under new management, that would be a good step.

I know some really sharp php developers.  One works at the company behind Wordpress.  He's learned all the traps in php, but the barrier to entry for php programming is just so very low that the average php program is ... er ... crap code.  Best to only stick with EXTREMELY well made code if php is the solution OR stick with languages that ahve a better history of trying to protect programmers from themselves and other users.

I'm still waiting for any other language to come close to the ["taint" checking in perl.]("http://search.cpan.org/~dapm/perl-5.10.1/pod/perlsec.pod#Taint_mode")

Oh - and the concerns over PHP aren't just mine.  The OWASP group (Open Web Application Security Project) says this:
> Serious issues abound in all aspects of PHP, making it difficult to write secure PHP applications. If you&#8217;re forced to use PHP, then you must be aware of all its pitfalls.
[https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)

Even professional php developers have trouble with security: [http://www.zdnet.com/wordpress-attack-highlights-30-million-targets-7000014256/](http://www.zdnet.com/wordpress-attack-highlights-30-million-targets-7000014256/)  Every year (approximately), there is a major php-based tool that gets hacked. They are the Microsoft of scripting languages, IMHO.

BTW, the website for my company is currently php and has been for years. When it was deployed by the CEO's brother, we sat down and explained that we couldn't stop it from being hacked - all we could do what have a response for "after" that occurs. The CEO wasn't happy. Actually, he was pissed.  There isn't anything on the public website that couldn't be done mostly with CSS and extremely lite JS, if any.  I reproduced it using Template::Toolkit and static files that built the pages to appear like dynamic stuff.  Matching headers, footers and sidebars are relatively trivial in TT (actually **ttree** is the tool name).  I still use TT to build some internal webpages - it is a simple, but extremely powerful language. [http://template-toolkit.org/docs/tutorial/Web.html](http://template-toolkit.org/docs/tutorial/Web.html)  Of course, there are many similar tools that will build a static website that doesn't look or behave like a static website.

---

### Post by Drone4four on 2014-04-01
In the the future, when I want to protect my content, I could password protect it as demonstrated at [this](http://angeles4four.wordpress.com/2014/03/31/lorem-ipsum-ra/) blog post.  The password is gizelle. 

I can also use this tag, these attributes and these values:
<meta name='robots' content='noindex,nofollow' />

I&#8217;ll use the following CSS rules:
```
-webkit-user-select: none; 
-khtml-user-select: none; 
-moz-user-select: none; 
-ms-user-select: none; 
-o-user-select: none; 
user-select: none;
```

Thanks to SeijiSensei, I can also append some provisions to my apache configuration file:
> **SeijiSensei said:**
> Instead of placing "nofollow,noindex" in a <meta> tag on each page, you can tell Apache to send these restrictions in advance of delivering the page content like this:
```

Header set "X-Robots-Tag" "noindex,nofollow"

```
To set this globally, add it to the bottom of /etc/apache2/apache2.conf right above the "IncludeOptional" directives.

It&#8217;s a dog-eat-dog security arms race out there. [The internet is a fragile piece of technology.](http://techcrunch.com/2014/03/29/the-internet-is-held-together-with-bubble-gum-and-baling-wire/)  The NSA and the Chinese Communist Party could easily circumvent the protective measures I listed above.  So could CyberPunk script kiddies.  But I don&#8217;t have a problem with that because I am pronoid (checkout the Wikipedia entry for a fascinating read).  Then why would I wanna protect my content if I don&#8217;t mind the NSA knowing everything about me?  Because I want to prevent prospective employers from finding on Google traces of my controversial political beliefs which I intend on posting to my site.  I take my privacy very seriously, in particular when it comes to employment.  The listed measures should be sufficient to meet my needs.  My intended audience for my site is maybe two dozen people, most of whom aren&#8217;t smart enough to use Ctrl + U in firefox or chrome.

What do you folks think? Is there anything else I should consider?

> **m-dw said:**
> No-one else mentioned it, but if you want your content to remain private you could always restrict access with password protection.    Is this password protect feature like the one I demonstrated in my lorum ipsum post?

> If you're really paranoid you should also protect it with SSL so that no-one can pick up the encoded username/password in the http request headers.
Does this mean that I&#8217;d have to get each user to sign up for login credentials?  This is overkill I think for my needs.  My master plan all along was to have a business card with my URL and the password (without a username).  I would hand this business card out to people who I meet who want a way to connect with me on fbook without having to exchange a tiny scrap piece of paper with my contact information.  Once they get there, they can explore who I am.  I wouldn&#8217;t want to hassle my acquaintances with having each of them to create login credentials and all that jazz.

---

### Post by TheFu on 2014-04-01
For a trivial, personal website that you don't want the world to see automatically, just don't put the entry page at the top.  Bury it a little.

I haven't used apache in years to know the default locations, but 
/var/www/index.html can just exist with an <html></html> to stop most casual people.
Then make a directory /var/www/sasfwae8fs/ and put your website there.  If you want extra security, use virtualhosts - leave the default so everyone is sent to the empty page if they come with just the IP or [www.domain.TLD](www.domain.TLD)  ... but setup sas.domain.TLD/sasfwae8fs/ to hit your website/webapp.  Unless you or a visitor gets careless ... like by using a URL shortener or online bookmark tool, then it is unlikely that most of the world will find it.  Be certain to remind all the users that you would rather they didn't share the URL anywhere, with anyone else.

And you can add a basicsecurity password if you like.  Shared passwords always get known, however,

I used to have an online photo gallery that I shared with friends and family. Then someone posted a link on twitter or FB to it (I don't recall) and then all the web crawlers started hitting it. So much for my buried URL.  I changed the name and stopped sharing it.  The Firefox "awesome bar" isn't helping any of us either. Other browsers have the same thing - anything typed into there gets submitted to the search engine configured, so it won't be long before they know about it.

You'll want to watch the log files for unauthorized access and probably setup some analytics to see which parts of the website are being read at all.

---

### Post by m-dw on 2014-04-02
> **Drone4four said:**
> Is this password protect feature like the one I demonstrated in my lorum ipsum post?

I don't know enough to say whether your security is breakable, but if all you're interested in is stopping a webcrawler from mirroring your site then it will probably be enough.

> **Drone4four said:**
> Does this mean that I’d have to get each user to sign up for login credentials?  This is overkill I think for my needs.  My master plan all along was to have a business card with my URL and the password (without a username).  I would hand this business card out to people who I meet who want a way to connect with me on fbook without having to exchange a tiny scrap piece of paper with my contact information.  Once they get there, they can explore who I am.  I wouldn’t want to hassle my acquaintances with having each of them to create login credentials and all that jazz.

If you were paranoid about security I suspect getting each user to sign up would be a fairly basic measure to protect your data.  From your response I can see you're not so a simple shared access password would be OK, until it gets widely known.

Have you thought about using a QR code?  Is it just to direct your contacts to a popular social networking site implied by the term fbook, or does the site contain the information you want to share.  I haven't got a clue how you'd program it, but apparently a mechanism has been developed to log in using a QR code.

---

### Post by TheFu on 2014-04-02
Most QR codes are just URL redirectors.  If you use an external service (bit.ly, goo.gl, etc) then those guys capture the redirection traffic for their stats - violating your user's privacy.  If you setup a redirecting service yourself, fine, great.

It is possible to put more data inside - about 4k characters - depending on the size of the 2D barcode.

QR is great if your peeps use it with their smartphones.  Not so great for the rest of the world.

I've seen them used like business cards - but more and more are just URLs to other data. Sometimes that data is like a business card, but 99.9999% of the time, it is to a URL redirector, redirector, redirector for marketeing of things I don't want, need, or have any interest in. ;(  Burn me once ...

---

### Post by Drone4four on 2015-06-30
Why is [this thread]("http://ubuntuforums.org/showthread.php?t=2214166&page=2&highlight=nsa") closed? I would today like to make a follow up post.  Here is my follow up in a new thread.

I'm trying to conceal my content from Google, Bing and YaCy indices.  To achieve this I've added <meta name='robots' content='noindex,nofollow' /> to all my html.  This meta tag doesn't prevent the NSA from indexing my content, but I don't care about them or the Chinese Communist Party for that matter.  What I am trying to achieve is ensuring that when recruiters and prospective employers search for my name on Google, they don't stumble upon my website.

In the original thread, **TheFu** commented: > For a trivial, personal website that you don't want the world to see automatically, just don't put the entry page at the top. Bury it a little.  I haven't used apache in years to know the default locations, but* /var/www/index.html can just exist with an <html></html> to stop most casual people. Then make a directory /var/www/sasfwae8fs/ and put your website there. 
I know what **TheFu** means.  My question today is: would my content be better concealed by burying it further down a directory tree like in /var/www/html/[remotehost]/public_html/qwerty/uiop/asdf/[content_homepage]/index.html. I would only use this scheme with the intention of sharing it directly via private IM as a link.  With this scheme I wouldn't put the link on the face of a business card because that would make it difficult for people to type in the entire lengthy web address into their web browser.  For the business card I'm thinking about looking into setting up a QR code URL redirector, as was explained in the original thread.  

I'll also be looking into adding Header set "X-Robots-Tag" "noindex,nofollow" to my apapche2.conf.  I thought about adding a 
```
* {
-webkit-user-select: none; 
-khtml-user-select: none; 
-moz-user-select: none; 
-ms-user-select: none; 
-o-user-select: none; 
user-select: none;
}
``` rule to all my CSS.  Although at this point I think using such a rule isn't necessary.  I'm also not interested in asking visitors to create login credentials.  When my audience navigate to my content using Firefox and Chrome, my URL is submitted to their index.  To circumvent this I could change the directory structure every so often, revoking access to older links.  Then I'll have to change all my QR codes.  

There are all sorts of things to consider when evading public access and maintaining secrecy.  What do you folks think?

---

### Post by CharlesA on 2015-06-30
> **Drone4four said:**
> Why is [this thread]("http://ubuntuforums.org/showthread.php?t=2214166&page=2&highlight=nsa") closed? I would today like to make a follow up post.  Here is my follow up in a new thread.

Threads get auto closed after one year from their last post has passed. It helps prevent necro postings.

Anyway, I have merged your new thread with the old one to keep things together. :)

As for your question - I don't really know. Most search engines obey robots.txt but if you want to keep your site from being indexed, why not just require a password to view it?

---

### Post by Drone4four on 2015-06-30
> **CharlesA said:**
> As for your question - I don't really know. Most search engines obey robots.txt but if you want to keep your site from being indexed, why not just require a password to view it?

I thought about using a password, and making the password trivial and providing it on the business card.  I could figure out how to implement the password protect feature here: [https://angeles4four.wordpress.com/2014/03/31/lorem-ipsum-ra/](https://angeles4four.wordpress.com/2014/03/31/lorem-ipsum-ra/)

The password is 'gizelle'.  Is this what you were suggesting, **CharlesA**?

This protective measure won't stop malicious script kiddies from accessing my content, but it would do what I have set out to do which is prevent relatively technically illiterate job recruiters or prospective employers from accessing my controversial content.

---

### Post by CharlesA on 2015-06-30
I was thinking of just password protecting the entire site, so you'd get a "login required" box, but if you can do it from within wordpress itself, that might be an easier way to manage it.

---

