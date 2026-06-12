---
title: "Mycroft searchplugin for Firefox"
date: 2005-03-21
forum: The Cafe
---

### Post by jnoreiko on 2005-03-21
Perhaps someone's made one of these for searching the Ubuntu package list already, but a search of these forums doesn't show it, so here is one I've just made.

To use it, save the code as a plain text file called 'ubuntu.src' in Firefox's searchplugins folder and relaunch the app.
All it needs is an icon -- perhaps someone can make a masked PNG of the ubuntu logo for it?

And inclusion in the [Mycroft database](http://mycroft.mozdev.org/download.html) would be nice, but expect that whenever, they are majorly backed up...

```

# Mycroft Search Plugin for Mozilla, Firebird, Netscape 6+, Beonix browsers 
# Mycroft Homepage: http://mycroft.mozdev.org
#
# SearchSite: Ubuntu packages
# Status: Working Full
#
# Author: J Noreiko
# Created: 2005-03-21
#
# Country: WW
# Language: en
# Category: Computer
#
# Known issues: None. 
#

<search
 version="7.1"
 name="Ubuntu"
 description="Ubuntu packages"
 method="get"
 action="http://higgs.djpig.de/cgi-ubuntu/search_packages.pl"
 searchform="http://higgs.djpig.de/ubuntu/www/"
>

<input name="keywords" user>
<input name="searchon" value="names">
<input name="subword" value="1">
<input name="version" value="all">
<input name="release" value="all">

<interpret
  resultListStart='</h3>'
  resultListEnd="</ul>"
  resultItemStart="<li>"
  resultItemEnd="</li>"
>
  
</search>

<browser
  update=""
  updateIcon=""
  updateCheckDays="3"
>

```

---

### Post by bored2k on 2005-03-21
Sorry but, What is Mycroft ?

---

### Post by jnoreiko on 2005-03-21
Look at the top right-hand corner of your Firefox window -- there's a Google search box. But in fact, you can search using ANY engine you like there. For example, I have IMDB, perldoc, BBC news, etc.

See [here for a repository of plug-ins](http://www.mozilla.org/products/firefox/central.html#central-engines). 

Mycroft is the standard for the search plugins that Firefox reads to create the drop-down list. They are just little XML documents as above. It's also the name of the Mozdev project that hosts them.

---

### Post by bored2k on 2005-03-21
[QUOTE=jnoreiko]Look at the top right-hand corner of your Firefox window -- there's a Google search box. But in fact, you can search using ANY engine you like there. For example, I have IMDB, perldoc, BBC news, etc.

See [here for a repository of plug-ins](http://www.mozilla.org/products/firefox/central.html#central-engines). 

Mycroft is the standard for the search plugins that Firefox reads to create the drop-down list. They are just little XML documents as above. It's also the name of the Mozdev project that hosts them.[/QUOTE]
 Oh, awsome, IMDB, uhhh, sexy.

Thanks, try that ASAP.

---

### Post by kassetra on 2005-03-21
[QUOTE=jnoreiko]All it needs is an icon -- perhaps someone can make a masked PNG of the ubuntu logo for it?[/QUOTE]

heee heee.  :)
[img]http://www.linuxpeach.com/ubuntu.png[/img]

I just put this little icon (as named) into the search plugins with the src file.  :)

---

### Post by cdhotfire on 2005-03-21
nice job dude.[img]http://www.ubuntuforums.org/images/smilies/eusa_clap.gif[/img]

edit: i cheated and got the littel clapping thing to work. ;-)

---

### Post by jnoreiko on 2005-03-21
Thanks kassetra. 
Looks great in the drop-down menu now. :)

I wonder if it's too late to suggest it be bundled in with firefox in hoary?

---

