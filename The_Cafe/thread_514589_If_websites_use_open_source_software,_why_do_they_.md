---
title: "If websites use open source software, why do they never reveal their source?"
date: 2007-07-31
forum: The Cafe
---

### Post by altonbr on 2007-07-31
If websites use open source software, why do they never reveal their source code? It's under the GPL to release source code when adding or editing software under the GPL, but not for people that USE the software. This makes sense of course and I'm not going to argue with why...

My question is, if millions use Python, PHP, Linux, Apache, Perl, MySQL, etc., how come no one ever releases source code of their websites?

I'm a Web Developer personally and wouldn't release my source code due to security risks but what else can people think of?

---

### Post by original_jamingrit on 2007-07-31
Using open source software and releasing open source software are two different things.  I'd assume that server-side scripts and stuff like that would be considered for private use, so they have no obligation to show us what's happening on their server.

---

### Post by Dr. C on 2007-07-31
Most FLOSS licenses do not require the release on source code  for websites. The Affero GPL does deal with this issue. 

[http://gplv3.fsf.org/agplv3-dd1-guide.html]("http://gplv3.fsf.org/agplv3-dd1-guide.html")

Compare the AGPL  with the GPL.

---

### Post by aysiu on 2007-07-31
If it's a simple website, you can at least *see* the code, if not appropriate it. Control-U in Firefox lets you see the source HTML of the page you're on.

---

### Post by altonbr on 2007-08-01
> **FineE said:**
> Most FLOSS licenses do not require the release on source code  for websites. The Affero GPL does deal with this issue. 

[http://gplv3.fsf.org/agplv3-dd1-guide.html]("http://gplv3.fsf.org/agplv3-dd1-guide.html")

Compare the AGPL  with the GPL.

Thanks for the link! Good read.

See, I was thinking of releases my source code (almost purely for fun) for all of my websites. I would have a link at the bottom of every website saying "Source Code" and it would take users to my company's Trac system.

The only thing is that the Trac system would have to be heavily moderated where every line of code that was added would be moderated, and even then, the site would never EVER be concurrent with the CVS.

Either that or turn off submissions no matter what and just let people view the code.

The 'security risks' I mentioned however, could be dire: If people know how your form is parsed, think of scripts they could write. So it's not guaranteed that a would fix be submitted by a or any user. 

I simply think it would be interesting for a website such as [http://sun.com](http://sun.com) to have open collaboration on their website.

---

### Post by igknighted on 2007-08-01
But people can already see how your forms are parsed more than likely.  I can view the source for the html/xhtml on a page, then see what scripts it points to and then either wget them or try to view them with a browser.  Nothing is ever really hidden on the web.  I suppose you could use some kind of pre-compiled scripts, but what major scripting language is compiled?  PHP, Perl, javascript, etc... none of these come pre-compiled to my knowledge.

---

### Post by altonbr on 2007-08-01
> **igknighted said:**
> But people can already see how your forms are parsed more than likely.  I can view the source for the html/xhtml on a page, then see what scripts it points to and then either wget them or try to view them with a browser.  Nothing is ever really hidden on the web.  I suppose you could use some kind of pre-compiled scripts, but what major scripting language is compiled?  PHP, Perl, javascript, etc... none of these come pre-compiled to my knowledge.

Since when can you download raw PHP source code?

---

### Post by igknighted on 2007-08-01
> **altonbr said:**
> Since when can you download raw PHP source code?

Look at the source code for the page, see the link in the form that calls the script, then just go wget it.  It should just be a text file.

EDIT: I believe the permissions on a PHP file must be 755 so you will have rights to view it and execute it (4=view, 1=execute).

---

### Post by forrestcupp on 2007-08-01
Anyway, you don't have to make source code available just because you *use* an open source software.  You're only required to make it available if you *distribute* the open source software for other people to use.

---

### Post by Hex_Mandos on 2007-08-01
Looking at the "source code" of a PHP page will show you PHP's HTML output, not the PHP source. What you see is what the browser considers source code, not what the PHP interpreter uses as source code.

In any case, what would be gained by open sourcing websites? I don't see why anyone would need the source code.

---

### Post by curuxz on 2007-08-01
If we are talking about open source websites i think it should apply to software like Joomla, whom money grabbing little "£%$£^ make "commercial" components that rely on opensource work. If they want a commercial component they should have to use a commercial CMS if they get paid everyone should vis versa. 

I would love to see the dropal, joomla, mambo etc licences changed to prohibit commercial components. They just arnt fair on opensource cms developers!

---

### Post by altonbr on 2007-08-12
> **forrestcupp said:**
> Anyway, you don't have to make source code available just because you *use* an open source software.  You're only required to make it available if you *distribute* the open source software for other people to use.

I understand that, but don't some software developers release their code because they want a) others to learn b) to help the community c) to show off how efficient they are, and/or d) get feedback from others because they need help with security issues?

> **Hex_Mandos said:**
> Looking at the "source code" of a PHP page will show you PHP's HTML output, not the PHP source. What you see is what the browser considers source code, not what the PHP interpreter uses as source code.

In any case, what would be gained by open sourcing websites? I don't see why anyone would need the source code.

Open source has allowed thousands upon thousands of programs learn certain programming languages, algorithms, etc. I don't see how it WOULD NOT benefit the public.

---

### Post by Tomosaur on 2007-08-13
If you're using open-source software on your web server, then that is not distribution of the software - the web page visitor generally never 'sees' the software, and so the site owner is not obligated to distribute the source. They're only using the software, not distributing it. They only ever see the output that the software creates. Many websites which use open-source software do in fact provide a link to where you can download said software (and thus get the source).

Even if the site owner modifies the original source, they're not obligated to release the modified source because it's normally considered to be for private use.

---

### Post by ssam on 2007-08-13
some websites do opensource their code.

[http://www.slashcode.com/](http://www.slashcode.com/) has the source code to slashdot.
[http://www.mediawiki.org/wiki/MediaWiki](http://www.mediawiki.org/wiki/MediaWiki) the wiki software for wikipedia

i think quite a few of the opensource content management systems, started off as just the code behind someones website.

the security is a weak argument. if your code is securely writen then it should not hurt to see the source code.

---

### Post by vexorian on 2007-08-13
> 
My question is, if millions use Python, PHP, Linux, Apache, Perl, MySQL, etc., how come no one ever releases source code of their websites?Because, as you said so, users are not forced to do that, only distributors are.

---

### Post by lingnoi on 2007-08-13
> **altonbr said:**
> If websites use open source software, why do they never reveal their source code? It's under the GPL to release source code when adding or editing software under the GPL, but not for people that USE the software.


You are wrong when you call the incoming internet requests users of GPL'd software because you are not using the GPL software, the company is. 

They are using it to give you html encoded pages to your web browser.

That does not make you a user of the GPL software because the software is running on their server not your computer and because of this fact they do not have to redistribute their private modifications under the GPL.

---

