---
title: "HOWTO: use gnome-dictionary offline (&amp; faster)"
date: 2006-03-17
forum: Tutorials
---

### Post by jjf on 2006-03-17
As a teacher, I find that gnome-dictionary and its applet are useful tools.  But at first it was much too slow and required Internet access.  Here are steps to install a database of definitions on your system so that gnome-dictionary works much faster and without Internet access.

*1. Install the packages **dictd**, **dict-gcide**, and **dict-wn**.*
  -- dictd is the dictionary database "server" of sorts
  -- dict-gcide is a comprehensive free English dictionary
  -- dict-wn is another dictionary with more up-to-date definitions, but it is not comprehensive

*2.  Install other dictionary packages you might want*
  -- Look in Synaptic at the many packages under **dict-** and read their descriptions.  If you want to download all the dictionaries, you can just get the metapackage **dict-freedict**.  I avoided this option because I did not want to clutter my definition screen or to wait while the program searched all these extra dictionaries I'd rarely (if ever) use.
 -- **dict-moby-thesaurus** is available if you want a thesaurus, too. 

*3.  Change the preferences in gnome-dictionary.*
  -- Applications > Dictionary opens gnome-dictionary
  -- Edit > Preferences
  -- change server to **localhost**
  -- change the Database to "search all databases"

*4.  work in progress: Change the order in which definitions appear*
  -- The file /etc/dictd/dictd.order apparently controls the order in which definitions are searched, the order in which they appear, or maybe both.  I want the up-to-date definition (from wn) to be listed first when they are available, so I changed my order to "wn gcide web1913..."  It does not appear to have made any difference -- the old-fashioned definition still appears first.

---

### Post by Thindi on 2007-07-29
Hi there!

May I ask what I have to do to change the Database to "search all databases"? I couldn't find anything about it and I haven't been using Linux for long, so I don't know much about it.
Thanks a lot!

---

### Post by izak on 2007-07-31
Excellent! Just as I what looking for: an off line thesaurus well integrated int gnome.

Maybe the interface is slightly different under Dapper, but to clarify,
launch the dictionary from Applications>Accessories>Dictionary. It can also be added to the panel by right clicking and select "add to panel".

Also, my preferences seem to behave/look slightly different. Once you open Edit>preferences, under the source tab, click Add. Double click Transport in the "Add Dictionary Source" window that pops up. This opens two additional text entry fields: "hostname" and "port". Change hostname from dict.org to localhost and your set to go. Leave port as it is.

---

### Post by larytet on 2007-11-19
confirmed in Ubuntu 7.04 - the Feisty Fawn

---

### Post by andrek on 2007-11-19
Thanks!

---

### Post by myharshdesigner on 2007-11-21
nice very nice :)

---

### Post by SteelCore on 2007-12-24
Thank you.  Just yesterday I added an entry to the ideapool requesting this offline dictionary feature.  I asked about it on the forums previously but got no answer.

---

### Post by prince_niceguy on 2008-02-04
Thanks mate!!! works like a charm on my laptop, I do not like lookup from internet it is slow...

---

### Post by Dr-KDE on 2008-03-03
Many thanks for this very good tutorial, which saves time and bandwith :) 
 
The same also applies to Kdict (KDE dict). The only difference in the steps is in step 3. 
  
Server configuration in Kdict is under   
settings->configure Dictionary->Server 
 
Other tips which apply to Kdict (not sure about gnome) is that you can highlight any word in any application and start Kdict through a keyboard shortcurt.  
 
Simply do the following 
 
1) in Kdict under settings->configure Dictionary->Miscellaneous. Check "define selected text on start" 
 
2) Assign a shortcut, using KDE menu editor create a keyboard shortcut to start kdict. For example you can use CTRL+ALT+W  as WordWeb if you are already used to this shortcut.

---

### Post by King_Louie on 2008-04-03
:grin: Thanks jjf! It works like a charm. I'll actually be using this now...

---

### Post by Maratonda on 2008-05-01
Does this work on the Terminal also?
For example: ```
dict ubuntu
```

---

### Post by hongleong on 2008-06-12
@ jjf: Thanks for the HowTo. It works for Hardy 8.04 too.
I've also tried to changed the sequence of the dictionaries in /etc/dictd/dictd.order. You're right. It doesn't change the query sequence in the dictionary program. Have you found the way to do that already?

@ Maratonda: Yes, "dict <word>" in terminal works fine too. :)

---

### Post by Tigera on 2008-06-12
It didn't work so well for me in Hardy, I'm afraid.  I selected the new source from the list and it gave me the error "Unable to find dictionary source".  How can I fix this?

---

### Post by hongleong on 2008-06-22
Tigera, are you sure you have installed dictd, dict-gcide and dict-wn successfully?

Check if dictd is running:

> ps -e | grep dictd

It has to be running for it to work.

---

### Post by bornagainpenguin on 2008-09-30
I just wanted to bump the thread up so others can add this to their laptops and other mobile devices!  Thanks Jff for a wonderful tip!

--bornagainpenguin

---

### Post by SteelCore on 2008-10-05
A friend of mine lately recommended using Stardict 
[http://en.wikipedia.org/wiki/Stardict](http://en.wikipedia.org/wiki/Stardict)
[http://stardict.sourceforge.net/](http://stardict.sourceforge.net/)
I found it to be very useful and with more functionality than GNOME-dictionary. An acceptable replacement for WordWeb that I was very relaiant upon in Windows xp.
I wonder why such small projects (gnome-dict and stardict) don't merge and form a stronger alliance? To be honest,both need quite some work in order to match the usability and presentation of WordWeb.

---

### Post by Simon-v on 2008-12-15
> **SteelCore said:**
> A friend of mine lately recommended using Stardict 
I wonder why such small projects (gnome-dict and stardict) don't merge and form a stronger alliance? To be honest,both need quite some work in order to match the usability and presentation of WordWeb.

Don't take my word, since i'm not one of them, but i think the GNOME devs believe StarDict is messy and doesn't comply with the quality standards they choose to follow.
I, personally, don't like the way StarDict looks and works. I would rather use something as clean and simple as gnome-dictionary together with dictd. Unfortunately, the dictionaries i need are currently only available for StarDict, so i'm stuck until either dictd learns to read StarDict dictionaries, gnome-dictionary learns to read StarDict dictionaries, it is replaced with a new app that can read StarDict dictionaries or a tool that can convert StarDict dictionaries to standard dict is developed. That, or StarDict gets its interface cleaned up. Don't know how likely is any of that, though.

---

### Post by da_excelsior on 2008-12-20
Thanks a lot.. 

working fine on intrepid.

---

### Post by rookworm on 2009-01-27
I tried all the steps, and i get "Error while looking up definition

Connection failed to the dictionary server at localhost:2628"

dict works from the command line for me, though.....


how do I go about troubleshooting this?

---

### Post by rookworm on 2009-03-27
well, got that working....

I'm still trying to figure out how to make it display the results from all installed databases simultaneously....

I set the gconf key "/apps/gnome-dictionary/database" to "!"

BUT, when i search for a term, it only displays the result from the first database on the list, with the same term listed many times in the "similar words" list on the sidebar.

before, when i looked up things from dict.org, all the definitions would be displayed at once.... How can I mimic this behaviour?

---

### Post by rookworm on 2009-03-31
just an update: I have installed the package "fantasdic", which is an overall amazing replacement for gnome-dictionary. Everything works to my liking; highly recommended.

---

### Post by manishmahabir on 2009-04-25
Fantasdic is wonderful.

if you add gnome-dictionary to panel, and then search a word, it will show results from all the dictionaries from dictd server.

---

### Post by tamim84 on 2009-05-02
Perfect solution..
And 'fantasdic' is a better client that gnome-dict in terms of functionality and configurability..but I found it's a tad slower than gnome-dict(while searching from local database)?

---

### Post by angelsniper45 on 2009-05-02
works great in 9.04 so far!! 

works fast to, great for when i have to write a paper.

---

### Post by Orlsend on 2009-05-02
I got all the packages mentioned above and I added the source like listed, Still it wont work. I am on jaunty 9.04.

---

### Post by s3a on 2009-05-08
Is there a way to add:

1) English Thesaurus?
2) French-French Dictionary?
3) French Thesaurus?

_apt-cache search only shows the following:_

deniz@debian:~$ apt-cache search dict-
dict - Dictionary Client
dict-bouvier - John Bouvier's Law Dictionary for the USA
dict-de-en - German-English translation dictionary for dictd
dict-devil - The Devil's Dictionary by Ambrose Bierce
dict-easton - Easton's 1897 Bible Dictionary
dict-elements - Data regarding the Elements
dict-foldoc - FOLDOC dictionary database
dict-freedict-afr-deu - Dict package for Afrikaans-German Freedict dictionary
dict-freedict-cro-eng - Dict package for Croatian-English Freedict dictionary
dict-freedict-cze-eng - Dict package for Czech-English Freedict dictionary
dict-freedict-dan-eng - Dict package for Danish-English Freedict dictionary
dict-freedict-deu-eng - Dict package for German-English Freedict dictionary
dict-freedict-deu-fra - Dict package for German-French Freedict dictionary
dict-freedict-deu-ita - Dict package for German-Italian Freedict dictionary
dict-freedict-deu-nld - Dict package for German-Dutch Freedict dictionary
dict-freedict-deu-por - Dict package for German-Portuguese Freedict dictionary
dict-freedict-eng-ara - Dict package for English-Arabic Freedict dictionary
dict-freedict-eng-cro - Dict package for English-Croatian Freedict dictionary
dict-freedict-eng-cze - Dict package for English-Czech Freedict dictionary
dict-freedict-eng-deu - Dict package for English-German Freedict dictionary
dict-freedict-eng-fra - Dict package for English-French Freedict dictionary
dict-freedict-eng-hin - Dict package for English-Hindi Freedict dictionary
dict-freedict-eng-hun - Dict package for English-Hungarian Freedict dictionary
dict-freedict-eng-iri - Dict package for English-Irish Freedict dictionary
dict-freedict-eng-ita - Dict package for English-Italian Freedict dictionary
dict-freedict-eng-lat - Dict package for English-Latin Freedict dictionary
dict-freedict-eng-nld - Dict package for English-Dutch Freedict dictionary
dict-freedict-eng-por - Dict package for English-Portuguese Freedict dictionary
dict-freedict-eng-rom - Dict package for English-Romanian Freedict dictionary
dict-freedict-eng-rus - Dict package for English-Russian Freedict dictionary
dict-freedict-eng-scr - Dict package for English-Serbo-Croat Freedict dictionary
dict-freedict-eng-spa - Dict package for English-Spanish Freedict dictionary
dict-freedict-eng-swa - Dict package for English-Swahili Freedict dictionary
dict-freedict-eng-swe - Dict package for English-Swedish Freedict dictionary
dict-freedict-eng-tur - Dict package for English-Turkish Freedict dictionary
dict-freedict-eng-wel - Dict package for English-Welsh Freedict dictionary
dict-freedict-fra-deu - Dict package for French-German Freedict dictionary
dict-freedict-fra-eng - Dict package for French-English Freedict dictionary
dict-freedict-fra-nld - Dict package for French-Dutch Freedict dictionary
dict-freedict-gla-deu - Dict package for Scottish Gaelic-German Freedict dictionary
dict-freedict-hin-eng - Dict package for Hindi-English Freedict dictionary
dict-freedict-hun-eng - Dict package for Hungarian-English Freedict dictionary
dict-freedict-iri-eng - Dict package for Irish-English Freedict dictionary
dict-freedict-ita-deu - Dict package for Italian-German Freedict dictionary
dict-freedict-ita-eng - Dict package for Italian-English Freedict dictionary
dict-freedict-jpn-deu - Dict package for Japanese-German Freedict dictionary
dict-freedict-lat-deu - Dict package for Latin-German Freedict dictionary
dict-freedict-lat-eng - Dict package for Latin-English Freedict dictionary
dict-freedict-nld-deu - Dict package for Dutch-German Freedict dictionary
dict-freedict-nld-eng - Dict package for Dutch-English Freedict dictionary
dict-freedict-nld-fra - Dict package for Dutch-French Freedict dictionary
dict-freedict-por-deu - Dict package for Portuguese-German Freedict dictionary
dict-freedict-por-eng - Dict package for Portuguese-English Freedict dictionary
dict-freedict-scr-eng - Dict package for Serbo-Croat-English Freedict dictionary
dict-freedict-slo-eng - Dict package for Slovak-English Freedict dictionary
dict-freedict-spa-eng - Dict package for Spanish-English Freedict dictionary
dict-freedict-swa-eng - Dict package for Swahili-English Freedict dictionary
dict-freedict-swe-eng - Dict package for Swedish-English Freedict dictionary
dict-freedict-tur-deu - Dict package for Turkish-German Freedict dictionary
dict-freedict-tur-eng - Dict package for Turkish-English Freedict dictionary
dict-freedict-wel-eng - Dict package for Welsh-English Freedict dictionary
dict-gazetteer - U.S. Gazetteer (1990)
dict-gazetteer2k - Placeholder package to install entire Gazetteer 2000
dict-gazetteer2k-counties - Counties Database for the 2000 US Gazetteer
dict-gazetteer2k-places - Places Database for the 2000 US Gazetteer
dict-gazetteer2k-zips - ZIP and ZCTA database for the 2000 US Gazetteer
dict-gcide - A Comprehensive English Dictionary
dict-hitchcock - Hitchcock's Bible Names Dictionary
dict-jargon - Jargon File 4.4.4
dict-moby-thesaurus - Largest and most comprehensive thesaurus
dict-stardic - An English to Chinese Dictionary
dict-vera - Dictionary of computer related acronyms -- dict format
dict-wn - electronic lexical database of English language for dict
dict-xdict - An English to Chinese Dictionary
dictd - Dictionary Server
dictem - Dict client for emacs
dictionary-el - dictionary client for Emacs
edict-el - An Emacs interface to Edict
edict-fpw - English / Japanese dictionary (formatted in JIS X 4081)
gnome-utils - GNOME desktop utilities
jed-extra - collection of useful Jed modes and utilities
kdict - dictionary client for KDE
latrine - curses-based LAnguage TRaINEr
predict - Satellite Tracking Program with Optional Voice Output
predict-gsat - Graphical Satellite Tracking Client Program
stardict-common - International dictionary - data files
stardict-gnome - International dictionary for GNOME 2
stardict-gtk - International dictionary written in GTK+ 2.x
stardict-plugin - International dictionary - common plugins
stardict-plugin-espeak - International dictionary - eSpeak TTS plugin
stardict-plugin-festival - International dictionary - Festival TTS plugin
stardict-plugin-gucharmap - International dictionary - gucharmap plugin
stardict-plugin-spell - International dictionary - spell plugin
stardict-tools - The dictionary conversion tools of stardict
stardict-xmlittre - French Littré dictionary for stardict
sword-dict-naves - Naves Topical Bible for SWORD
sword-dict-strongs-greek - Strong's Greek Bible Dictionary for SWORD
sword-dict-strongs-hebrew - Strong's Hebrew Bible Dictionary for SWORD
xfce4-dict - Dictionary plugin for Xfce4 panel
xfce4-dict-plugin - transitionnal dummy package for xfce4-dict
bgoffice-dict-downloader - download dictionaries for gbgoffice
opendict-plugins-lingvosoft - plugins for OpenDict - LingvoSoft Online Dictionaries
stardict-english-czech - Stardict package for English-Czech dictionary
deniz@debian:~$

---

### Post by oOarthurOo on 2009-05-19
I haven't gotten this working on Jaunty yet, has anyone else had success?

---

### Post by majikins on 2009-05-27
Hi

Yes I have - works fine on my setup.

M

---

### Post by oOarthurOo on 2009-05-27
Did you do anything different from the OP's post? Some of his instructions seem like they need to be modified for Jaunty

---

### Post by majikins on 2009-05-29
Hi

yes I deviated a bit - installed dictd, dict-gcide and dict-moby-theasaurus.  I then used fantasdic as the client.

S

---

### Post by legends2k on 2009-06-01
If you want a fast off-line thesaurus, you can try [Artha]("http://artha.sourceforge.net/"), which was specifically written for this on Linux, using GTK+. See here for details: [http://ubuntuforums.org/showthread.php?t=1065384](http://ubuntuforums.org/showthread.php?t=1065384)

---

### Post by santhust on 2009-06-16
confirmed in ubuntu 9.04 Jaunty

---

### Post by ssam on 2009-06-16
there is also [Aarddict]("http://aarddict.org/"). it has a couple of dictionary files.

---

### Post by kigali on 2009-07-03
I had some problems with running it in Jaunty 9.04, took me a while, but finally it looks like working.

I've put 127.0.0.1 instead of localhost. And I'm not sure if running sudo gnome-dictionary hasn't helped at some point.

And I recommend using it with gnome-do, it's very comfortable this way.

---

### Post by Trekky0623 on 2009-07-03
> **kigali said:**
> I had some problems with running it in Jaunty 9.04, took me a while, but finally it looks like working.

I've put 127.0.0.1 instead of localhost. And I'm not sure if running sudo gnome-dictionary hasn't helped at some point.

And I recommend using it with gnome-do, it's very comfortable this way.

Thank you, I was having trouble, and this fixed it.

---

### Post by lovejames on 2009-08-04
Thanks. Replacing localhost with 127.0.01 seems worked with me too. I've been struggling for long to get it sorted.

---

### Post by ssdt on 2009-08-04
Thanks for the tip. Will come handy for students like me.

---

### Post by barretr on 2009-08-18
Adding:

> 127.0.0.1	localhost

to /etc/hosts would also work. Thanks for the tip jjf.

---

### Post by silent_shade on 2009-08-26
Thanks for the howto and, particularly, for address correction! Finally made it work with 127.0.0.1

---

### Post by ntlam on 2009-09-22
> **santhust said:**
> confirmed in ubuntu 9.04 Jaunty

I just install ubuntu 9.04.

the dictionary is in application -> office instead of application --> accessories. (not a big deal)

I go to edit -> preferences -> add a new source, set it localhost. But there is no option to set database.

Any idea please?

Lam

---

### Post by ntlam on 2009-09-22
never mind. got it work by using 127.0.0.1 instead of localhost.

---

### Post by khughitt on 2009-09-23
> **ntlam said:**
> never mind. got it work by using 127.0.0.1 instead of localhost.

Yep. I ran into the same problem. There is a bug report relating to the issue here: [https://bugzilla.gnome.org/show_bug.cgi?id=595470](https://bugzilla.gnome.org/show_bug.cgi?id=595470).

Thanks for the great thread!

---

### Post by xiaoyong on 2009-11-25
> **jjf said:**
> 
*4.  work in progress: Change the order in which definitions appear*
  -- The file /etc/dictd/dictd.order apparently controls the order in which definitions are searched, the order in which they appear, or maybe both.  I want the up-to-date definition (from wn) to be listed first when they are available, so I changed my order to "wn gcide web1913..."  It does not appear to have made any difference -- the old-fashioned definition still appears first.

Edit /var/lib/dictd/db.list and adjust the order of dictionaries.  After reboot you will see the order has been changed.  You also can disable the access of inetd server via editing /etc/dictd/dictd.conf

---

### Post by reddox on 2009-11-26
Thanks for this!

Had to change 'localhost' to 127.0.0.1 to make it work..

---

### Post by airtonix on 2010-02-17
thread author needs to change their original post so that copy pasting the package names doesn't cause me to rage.

```
sudo apt-get install dictd dict-gcide dict-wn
```

1. this isn't one of your class lessons where you sneakingly leave out key elements in an effort to make us be proactive
2. if you're going to bother bolding the package names to make it ***easier***... then you should have just created the code block i made above.
3. do not ever put $ at the start of your 'oh lol see this here ??? lololol its a terminal command lolol"... its just annoying.

/rage

Also after following every suggestion here in this thread gnome-dictionary still does not want to use local database.

---

### Post by gvlists on 2010-04-18
> **legends2k said:**
> If you want a fast off-line thesaurus, you can try [Artha]("http://artha.sourceforge.net/"), which was specifically written for this on Linux, using GTK+. See here for details: [http://ubuntuforums.org/showthread.php?t=1065384](http://ubuntuforums.org/showthread.php?t=1065384)

Thank you. Gnome-dictionary is almost not usable for me as I am travelling most of the time. I do not see the option of localhost in preferences. Anyway artha came to help. May be it is a wordweb hangover. The shortcut and notification feature of artha fits my requirement better. Thanks again.

---

### Post by daqron on 2010-05-17
> **airtonix said:**
> thread author needs to change their original post so that copy pasting the package names doesn't cause me to rage.
Dude, calm down. Anyone who takes time to post stuff that helps other people deserves appreciation, not rage. Your code block is indeed helpful, so thank you for contributing that to the discussion.

Thanks everyone. This works great in Lucid, using 127.0.0.1 as the host.

---

### Post by mescobal on 2010-11-12
Works OK un 10.10 with 127.0.0.1 as server.
Configuration dialogs could be better (ie it would be nice to edit entries. You should delete and create one to change settings).
Marcelo.

---

### Post by silentstone on 2010-11-13
Thanks for the tip on using offline sources with gnome-dictionary.  It works fine on Lucid Lynx (10.04), although I don't get an applet on Netbook Remix.  An earlier suggestion, Artha (offers definitions, parts of speech, and thesaurus) works better with global shortcuts and a systray icon.

Another alternative is GoldenDict: [http://goldendict.org/screenshots.php](http://goldendict.org/screenshots.php)  GoldenDict offers that plus grouping of multiple dictionaries and quick switching between those, simultaneous offline/online dictionary sources, audio play, and adding any website or file as a source.  On a GNOME desktop, Artha is better, but for sheer volume of features, GoldenDict takes the cake, and isn't too bad running QT4 interface on GNOME desktop.  It's in the Ubuntu repos.

---

### Post by kanishkdudeja on 2010-11-30
it worked. thanks a lot mate. :)

---

### Post by jdy on 2010-11-30
that's great ,change the traditional patterns,and more faster

---

### Post by linwhwylb on 2010-12-07
Thanks! It helps me.

---

### Post by anilg on 2010-12-24
I had a similar need as the original posted, and so went and wrote glance.

[http://www.gulecha.org/2010/12/24/glance-better-word-lookup/](http://www.gulecha.org/2010/12/24/glance-better-word-lookup/)

---

### Post by leomeloxp on 2011-03-10
Hello everyone, I managed to use the dictionary by changing localhost to 127.0.0.1 on Lucid 10.04. Problem is, I can't choose to use all the dictionaries at the same time.

I can choose any of them individually and the other results appear as similar words, but they won't show on the same definition =X

If anyone can help, thanks =]

---

### Post by xiaoyong on 2011-03-12
> **jjf said:**
> *4.  work in progress: Change the order in which definitions appear*
  -- The file /etc/dictd/dictd.order apparently controls the order in which definitions are searched, the order in which they appear, or maybe both.  I want the up-to-date definition (from wn) to be listed first when they are available, so I changed my order to "wn gcide web1913..."  It does not appear to have made any difference -- the old-fashioned definition still appears first.

After change the order in /etc/dictd/dictd.order, need to execute
# sudo dictdconfig -w

Then, the file /var/lib/dictd/db.list is updated.  Restart dictd and enjoy it.

---

### Post by harpinder on 2011-08-15
i have installed the above said packages in my ubuntu 11.04 but there is no icon of dictionary in accessories.please help me .where is the icon how to use the dictionary.

---

### Post by astrobob.tk on 2012-08-25
Indeed;  In 10.04, I had the dictionary applet for the gnome-panel installed so that I have quick access to dictionary; I am not sure, however,how to do this in 12.04 (i.e; have the applet in the panel!)?  Help is appreciated  thanks

---

### Post by ubu21 on 2012-08-25
> **silentstone said:**
>  Another alternative is GoldenDict: [http://goldendict.org/screenshots.php](http://goldendict.org/screenshots.php)  GoldenDict offers that plus grouping of multiple dictionaries and quick switching between those, simultaneous offline/online dictionary sources, audio play, and adding any website or file as a source.  On a GNOME desktop, Artha is better, but for sheer volume of features, GoldenDict takes the cake, and isn't too bad running QT4 interface on GNOME desktop.  It's in the Ubuntu repos.

Goldendict is a great software. Initially I wanted to get gnome-dictionary (probably obsolete by the time I write this post) to work with the "search all databases" option as stated in the original post. I was unable to find this option on my Ubuntu 12.04 x64, and started to look for any workarounds. Google pointed me to this post. The only solution that I have found was:

#apt-get install goldendict goldendict-wordnet

and then launch the application via Dash Home -> goldendict. The first time it starts, this application makes an inventory of all other locally available dictionaries, running through dictd server. Me, I had many of them, since I had installed all free dictionaries of English + French + German I had found, by running:

# apt-get install dict-freedict-eng-fra dict-freedict-fra-eng dict-freedict-eng-rom dict-freedict-eng-deu dict-freedict-fra-deu dict-freedict-deu-eng dict-freedict-deu-fra dict dict-gcide dict-wn wbritish-large  wfrench wamerican-large trans-de-en dict-moby-thesaurus dictionaries-common iamerican ifrench dictd wordnet

---

### Post by astrobob.tk on 2012-08-26
Thanks for the suggestion, but my solution is still not solved!

All I need is an always-ready applet "in the panel" when I want to search for a word (preferably, gnome-dictionary-applet); I do not want to open over & again a software every time I want to search for a word!

thanks again

---

