---
title: "Firefox 2.0 Alpha Available"
date: 2006-03-20
forum: The Cafe
---

### Post by hod139 on 2006-03-20
I haven't seen this posted anywhere yet. In case you don't know mozilla has made firefox 2.0 alpha [available for download]("http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha1/linux-i686/en-US/bonecho-alpha1.tar.gz").  I'm downloading it now.  If you have tried it, what are your thoughts.

** Edit**: Today Mozilla "officially" released the alpha version.  I have updated my previous link.  The dowload site for all platforms can be found here: 
[http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha1/]("http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha1/")
To test the alpha release without actually "installing" into your system, extract the tarball and run ./firefox:       
```

tar -xzvf bonecho-alpha1.tar.gz
cd firefox
./firefox

```

---

### Post by hod139 on 2006-03-20
I used [this guide]("https://wiki.ubuntu.com/FirefoxNewVersion") to install the alpha version, making the appropriate changes where necessary.  I am writing this post using the alpha version, and so far so good.  The new places menu is really nice.

---

### Post by mstlyevil on 2006-03-20
I noticed reading the Wiki that one of the stated goals was a new icon set to match the default Gnome enviroment.

---

### Post by GeneralZod on 2006-03-20
Do note that this is not a proper release (I mean it's not in an official *alpha* release; this is no different from the standard Firefox Nightlies that are released every ... night).  It's one of these weird non-stories that seem to be being mis-reported on every tech news site in the world, for some reason :) 

Here's Asa:

[QUOTE=Asa Dotzler]
Just in case there's anyone reading who doesn't already know this:

When we make a new release, we'll say so. Please don't report new releases because someone checks in a change to the user agent or similar. If we're actaully doing a release, we'll announce it. Thanks.
[/QUOTE]

[http://weblogs.mozillazine.org/asa/](http://weblogs.mozillazine.org/asa/)

---

### Post by WildTangent on 2006-03-20
Well, official alpha or not, I'm using it anyway. I love the close button on each tab. :D So much more convenient

-Wild

---

### Post by hod139 on 2006-03-20
> **GeneralZod]Do note that this is not a proper release (I mean it's not in an official *alpha* release said:**
> http://weblogs.mozillazine.org/asa/[/URL]

Official or not, it's out there and anyone can try it.

---

### Post by mstlyevil on 2006-03-20
[QUOTE=WildTangent]Well, official alpha or not, I'm using it anyway. I love the close button on each tab. :D So much more convenient

-Wild[/QUOTE]

I just use the Tabx extention in FF 1.5 to get the same function. I will wait until it is a beta before I decide to install it myself.

---

### Post by GeneralZod on 2006-03-20
[QUOTE=hod139]Official or not, it's out there and anyone can try it.[/QUOTE]

Oh sure, I only mentioned this as there's nothing special about  this release from Mozilla's point of view, nor will it be any less buggy than any other nightly releases.  I think more people will be inclined to try it if it sounds like an official release, and this could lead to disappointment.

---

### Post by hod139 on 2006-03-20
[quote=GeneralZod]Oh sure, I only mentioned this as there's nothing special about  this release from Mozilla's point of view, nor will it be any less buggy than any other nightly releases.  I think more people will be inclined to try it if it sounds like an official release, and this could lead to disappointment.[/quote]

Good points.  This release is bound to be buggy, but there are always users who like living  on the bleeding edge.

---

### Post by GoA on 2006-03-20
Currently testing it nothing special for me, only notice the new close tab buttons.

---

### Post by public_void on 2006-03-21
Seems alot of people thought it was a new release.

From [Wired News](http://blog.wired.com/monkeybites/)
> It was reported yesterday on TechCrunch that Mozilla had released an alpha version of Firefox 2.0. Digg and Slashdot immediately picked up on the story, and some users noticed that the two main blog sites linked to in the various posts from TechCrunch and elsewhere were actually offering links to Tinderbox releases of the browser — periodical builds with many bugs meant for developers. 

So is this the new alpha of Firefox or what? The short answer is no. You shouldn't install it unless you want a problematic browser with no extension support. As Asa Dotzler says on MozillaZine: 

When we make a new release, we'll say so. Please don't report new releases because someone checks in a change to the user agent or similar. If we're actually doing a release, we'll announce it. Thanks.

Simple enough, right? Well, that didn't stop thousands of users from downloading and installing the Tinderbox version of the browser anyway. Many of them promptly started complaining about broken features, bugs, and other problems. Well, if you didn't download it from Mozilla directly, then it's not an official release...

The word on the street is that Mozilla is planning on releasing a stable alpha (or at least a more stable alpha) of Firefox 2.0 tomorrow, the 21st. Keep checking the official site for any release announcements.


---

### Post by jasplund on 2006-03-21
[QUOTE=WildTangent]Well, official alpha or not, I'm using it anyway. I love the close button on each tab. :D So much more convenient

-Wild[/QUOTE]
I just use middleclick to close tabs. I don't want a button for it

---

### Post by hod139 on 2006-03-22
Looks like it is now [official.]("http://www.mozilla.org/projects/bonecho/releases/2.0a1.html")
Here is the link to the official release: [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha1/linux-i686/en-US/]("http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha1/linux-i686/en-US/")

To install, extract the tarball and run ./firefox:       
```

tar -xzvf bonecho-alpha1.tar.gz
cd firefox
./firefox

```

List of changes:
[LIST]
[*]Changes to tabbed browsing behavior
[*]New data storage layer for bookmarks and history (using SQLlite)
[*]Extended search plugin format
[*]Updates to the extension system to provide enhanced security and to allow for easier localization of extensions
[*]Support for SVG text using svg:textPath
[*][List of notable bug fixes]("http://www.squarefree.com/burningedge/releases/2.0a1.html") [/LIST]

---

