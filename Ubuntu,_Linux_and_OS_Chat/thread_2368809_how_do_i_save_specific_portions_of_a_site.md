---
title: "how do i save specific portions of a site"
date: 2017-08-15
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2017-08-15
This is the site I'm trying to save for offline viewing: [http://en.uesp.net/wiki/Morrowind:Morrowind](http://en.uesp.net/wiki/Morrowind:Morrowind) and all related links.

However, all the solutions I've found seems to save [http://en.uesp.net](http://en.uesp.net) in it's entirety instead.

I'd like to save only specific portions from the site, specifically pages with this address only [http://en.uesp.net/wiki/Morrowind:](http://en.uesp.net/wiki/Morrowind:) and not all of [http://en.uesp.net](http://en.uesp.net).

How do I do this?

---

### Post by dragonfly41 on 2017-08-15
I believe that webhttrack (in Ubuntu Software Centre) does this.

```
sudo apt-get install webhttrack
```

Launch from command terminal .. webhttrack .. and new browser window appears.

Or there is a launcher Browse Mirrored WebSites in Internet menu category.

Added documentation link .. [http://www.linux-magazine.com/Online/Features/WebHTTrack-Website-Copier](http://www.linux-magazine.com/Online/Features/WebHTTrack-Website-Copier)

Refer to usage of filters for selective downloads.

---

### Post by ardouronerous on 2017-08-15
I've already tired this, it saves the entire website.
Could you give me some instructions on how to use this for my purposes?

---

### Post by dragonfly41 on 2017-08-15
I thought that setting filters might serve this purpose ..

[https://www.httrack.com/html/filters.html](https://www.httrack.com/html/filters.html)

---

### Post by ardouronerous on 2017-08-15
The filters only filter's out the file types, not specific paths.

---

### Post by SeijiSensei on 2017-08-15
I'd use wget with the -i option and a list of the specific URLs you want to download.  For instance,

```

http://en.uesp.net/wiki/Morrowind:Shrines
http://en.uesp.net/wiki/Morrowind:Spell_Effects
[etc.]

```

You can easily pull these from the output of "wget -r http://en.uesp.net/wiki/Morrowind:Morrowind".

---

### Post by dragonfly41 on 2017-08-15
webhttrack may not be the easiest tool to use but as an experiment I find that if you explicitly exclude pages you can get a partial download.

These are derived filters I experimented with .. (no doubt a script could be written to get these patterns from menu links)

```

 -*Main*
-*Featured* 
-*Recent*
-*Random*
-*How*
-*Help*
-*wikiredirect*
-*All*
-*Lore*
-*Books*
-*Legends*
-*Online*
-*Skyrim*
-*Oblivion*
-*Redguard*
-*Battlespire*
-*Daggerfall*
-*Arena*
-*TES*
-*UESP*
-*discord*
-*facebook*
-*google*
-*tumblr*
-*twitter*
-*General*
-*WhatLinksHere*
-*Special*
-*printable*
-*oldid*

+[http://en.uesp.net/wiki/Morrowind:Morrowind](http://en.uesp.net/wiki/Morrowind:Morrowind)


```

---

### Post by ardouronerous on 2017-08-15
> **SeijiSensei said:**
> I'd use wget with the -i option and a list of the specific URLs you want to download.  For instance,

```

http://en.uesp.net/wiki/Morrowind:Shrines
http://en.uesp.net/wiki/Morrowind:Spell_Effects
[etc.]

```

You can easily pull these from the output of "wget -r http://en.uesp.net/wiki/Morrowind:Morrowind".

Listing all of [http://en.uesp.net/wiki/Morrowind:](http://en.uesp.net/wiki/Morrowind:) would take too long though.

> **dragonfly41 said:**
> webhttrack may not be the easiest tool to  use but as an experiment I find that if you explicitly exclude pages you  can get a partial download.

These are derived filters I experimented with .. (no doubt a script could be written to get these patterns from menu links)

```

 -*Main*
-*Featured* 
-*Recent*
-*Random*
-*How*
-*Help*
-*wikiredirect*
-*All*
-*Lore*
-*Books*
-*Legends*
-*Online*
-*Skyrim*
-*Oblivion*
-*Redguard*
-*Battlespire*
-*Daggerfall*
-*Arena*
-*TES*
-*UESP*
-*discord*
-*facebook*
-*google*
-*tumblr*
-*twitter*
-*General*
-*WhatLinksHere*
-*Special*
-*printable*
-*oldid*

+[http://en.uesp.net/wiki/Morrowind:Morrowind](http://en.uesp.net/wiki/Morrowind:Morrowind)


```

I've been trying to figure out HTTrack all night, sorry, I couldn't understand it, too complex for me.

At this point, I'm giving up on this, unless there are easier alternatives out there, I've been looking and it all points to HTTrack.

I've found this while Googling for solutions, and apparently HTTrack isn't good for my purposes.

[https://stackoverflow.com/questions/538865/how-do-you-archive-an-entire-website-for-offline-viewing/539025#539025](https://stackoverflow.com/questions/538865/how-do-you-archive-an-entire-website-for-offline-viewing/539025#539025)
 > I've been using HTTrack for several years now.  It handles all of the  inter-page linking, etc. just fine.  **My only complaint is that I  haven't found a good way to keep it limited to a sub-site very well.   For instance, if there is a site [www.foo.com/steve](www.foo.com/steve) that I want to  archive, it will likely follow links to [www.foo.com/rowe](www.foo.com/rowe) and archive  that too.**  Otherwise it's great.  Highly configurable and reliable.

---

### Post by dragonfly41 on 2017-08-16
[COLOR=#000000]> and apparently HTTrack isn't good for my purposes.

I got it to work. I think you need to understand how to define filters.
[/COLOR]Perhaps I did not explain how I derived the list of shortened filters.

e.g. -*Main*

I used the wildcard &#8220;*&#8221; to shorten the search pattern for each link.

But let us take the full URL's instead.

Go to the main web site ...  [http://en.uesp.net/wiki/Main_Page](http://en.uesp.net/wiki/Main_Page) ... in your browser.
In my shortened list I simply used "Main" as the pattern but you can use the full URL

Now look at the menu list to the left of the page.

The following exercise is needed only once.

Right click on each menu link starting at &#8220;Main Page&#8221;.

Right click on the menu link and from content menu select "Copy link address".

Paste into a fresh text editor page.

Repeat with all other menu links.

Run through the list and add character &#8220;-&#8221; to the beginning of each link.
You are creating the list to skip.

The links you wish to retain are ..

Morrowind
Tribunal
Bloodwind

These links can be saved at bottom of list with prefix &#8220;+&#8221;.

So at the end of this exercise which takes a few minutes, save the text file as links.txt.

Now you can either launch httrack (the command line version) or
webhttrack (the gui) to spawn a browser session.  The workflow below assumes use of webhttrack.

When you click on &#8220;next >>&#8221; the second time you see a form where you can add filter patterns

OR there is an option to import URL lists as a text file (this is the list of links you created previously).

Also when you installed httrack with the command

```
sudo apt-get install webhttrack httrack
```

There is an optional package httrack-doc which can be installed.   If this is installed you can click on &#8220;Click to get help!&#8221; link at any stage in using webhttrack.

...

There should be an easier way to compile the blacklist and whitelist rules for any site.

I'm looking at python scrapy to see how that might be done. But meanwhile the above does work.

---

### Post by SeijiSensei on 2017-08-16
> **ardouronerous said:**
> Listing all of [http://en.uesp.net/wiki/Morrowind:](http://en.uesp.net/wiki/Morrowind:) would take too long though.
```
wget -r http://en.uesp.net/wiki/Morrowind:Morrowind --spider 2>&1 | grep '2017' | grep 'wiki/Morrow' | grep  saved  | awk '{print $6}' 
```

---

### Post by ardouronerous on 2017-08-16
> **dragonfly41 said:**
> [COLOR=#000000]

I got it to work. I think you need to understand how to define filters.
[/COLOR]Perhaps I did not explain how I derived the list of shortened filters.

e.g. -*Main*

I used the wildcard “*” to shorten the search pattern for each link.

But let us take the full URL's instead.

Go to the main web site ...  [http://en.uesp.net/wiki/Main_Page](http://en.uesp.net/wiki/Main_Page) ... in your browser.
In my shortened list I simply used "Main" as the pattern but you can use the full URL

Now look at the menu list to the left of the page.

The following exercise is needed only once.

Right click on each menu link starting at “Main Page”.

Right click on the menu link and from content menu select "Copy link address".

Paste into a fresh text editor page.

Repeat with all other menu links.

Run through the list and add character “-” to the beginning of each link.
You are creating the list to skip.

The links you wish to retain are ..

Morrowind
Tribunal
Bloodwind

These links can be saved at bottom of list with prefix “+”.

So at the end of this exercise which takes a few minutes, save the text file as links.txt.

Now you can either launch httrack (the command line version) or
webhttrack (the gui) to spawn a browser session.  The workflow below assumes use of webhttrack.

When you click on “next >>” the second time you see a form where you can add filter patterns

OR there is an option to import URL lists as a text file (this is the list of links you created previously).

Also when you installed httrack with the command

```
sudo apt-get install webhttrack httrack
```

There is an optional package httrack-doc which can be installed.   If  this is installed you can click on “Click to get help!” link at any  stage in using webhttrack.

...

There should be an easier way to compile the blacklist and whitelist rules for any site.

I'm looking at python scrapy to see how that might be done. But meanwhile the above does work.

I tried it again as you suggested, but it still saves unwanted stuff, so  this leads me to believe I have to list out all the links I don't want  which would take me a long time.

I wish there was an easier way to do this.

> **SeijiSensei said:**
> ```
wget -r http://en.uesp.net/wiki/Morrowind:Morrowind --spider 2>&1 | grep '2017' | grep 'wiki/Morrow' | grep  saved  | awk '{print $6}' 
```

Hi.
Can you explain what this code is suppose to do? Thanks :)

---

### Post by SeijiSensei on 2017-08-17
Did you try running it yourself?  It will create a list of all the links you want.

```

&#8216;en.uesp.net/wiki/Morrowind:Morrowind&#8217;
&#8216;en.uesp.net/wiki/Morrowind:Vvardenfell&#8217;
&#8216;en.uesp.net/wiki/Morrowind:Dunmer&#8217;
&#8216;en.uesp.net/wiki/Morrowind:Quests&#8217;
&#8216;en.uesp.net/wiki/Morrowind:Official_Add-Ons&#8217;
&#8216;en.uesp.net/wiki/Morrowind:Attributes&#8217;
&#8216;en.uesp.net/wiki/Morrowind:Birthsigns&#8217;
[etc.]

```

You just need to dump the results to a file, edit out the quotes, and hang an "http://" in front of each entry.

---

### Post by ardouronerous on 2017-08-17
@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195"): I did what you suggested.

It did download the subsite, however, the downloaded html files are not linked to each other, so when I was trying them offline, the response I got was 'file not found'.

---

### Post by SeijiSensei on 2017-08-18
Show us a sample URL that does not link to its target.  Maybe there is an easy fix.

---

### Post by ardouronerous on 2017-08-18
I saved the html files here: */home/~/Documents/wiki/*

I checked on */home/~/Documents/wiki/Morrowind:Morrowind*, it opened up Firefox.

But when I try to click on, for example, Master Trainers, this is the result:

```
file:///wiki/Morrowind:Master_Trainers
File not found

Firefox can’t find the file at /wiki/Morrowind:Master_Trainers.

    Check the file name for capitalisation or other typing errors.
    Check to see if the file was moved, renamed or deleted.
```

---

### Post by dragonfly41 on 2017-08-18
ardouronerous

I suspect that you will need to go to your downloaded files
in ~/Downloads/wiki/ and right click on each file to open context menu
and ..  open with .. your Web Browser

...

If you can clarify if you are more interested in text than images
I can suggest yet another tool to try .. used for semantic analysis.

This is a powerful tool but I will not go down that route unless you are interested.

---

### Post by SeijiSensei on 2017-08-18
It looks like the documents have absolute versus relative links.  The URL
```
file:///wiki/Morrowind:Master_Trainers
```
is looking for a directory off the root of the filesystem called /wiki.

You can probably fix this with a symbolic link:
```

cd /
sudo ln -s /home/ardouronerous/Documents/wiki

```

See if that helps.

---

### Post by ardouronerous on 2017-08-18
[COLOR=#000000]@[/COLOR][COLOR=#000000]**[COLOR=#000000]dragonfly41[/COLOR]**[COLOR=#000000] [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][COLOR=#000000][COLOR=#000000][/COLOR][/COLOR]I believe you are correct, I will have to live with just going through the files in Thunar.[/COLOR][/COLOR]
i do need the images, because I have to download other game walkthroughs and some of them require images to help guide gamers.

@**[COLOR=#000000]SeijiSensei [/COLOR]**[COLOR=#000000]it does help in linking the html files, but it's not very flexible, if you move the /wiki/ to another directory or location, it loses it's connectivity.[/COLOR]

I guess I'll have to manually link them every time I need to change directories.

Thanks for the help guys :)

---

