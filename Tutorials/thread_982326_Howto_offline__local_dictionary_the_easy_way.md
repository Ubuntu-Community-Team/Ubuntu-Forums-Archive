---
title: "Howto: offline / local dictionary the easy way"
date: 2008-11-14
forum: Tutorials
---

### Post by jon.reeve on 2008-11-14
I searched all over to find an offline dictionary solution to meet my needs, since I'm often in need of a dictionary and thesaurus I can use offline. Having not found an adequate solution in OpenDict (its dictionaries are only for foreign languages like Latvian and its website is inundated with spam), Stardict (it's bloated, written in bad English, and generally annoying to use) or other programs, and not always having access to the internet whenever I need a dictionary, I figured out how to set up a local DICT server and thereby use the Dictionary program that's already included with Ubuntu to access locally stored dictionaries. It's not all that difficult, it turns out. 

First, install DictD: 

```
sudo apt-get install dictd

```
this installs a DICT server. now you can install whatever dictionaries you want. Dictionaries are in the repos, here's a list I found using a package search: 

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=dict](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=dict)

so to install a thesaurus, for example, use
```

sudo apt-get install dict-moby-thesaurus
```

Now to configure Dictionary, open the Dictionary program (in <Hardy it's in Accessories, in Intrepid it's under Office), go into Edit -> Preferences, click on "Add" to add a source, then under "Description" give it a name like "Local Dictionaries," under "hostname" type "localhost" [EDIT: In Jaunty and later you might try putting "127.0.0.1" (without the quotes) instead; see below] and leave the port number the same. Now click "add" and now whenever you're offline you can choose "Local Dictionaries" from "Dictionary Sources" and access your dictionaries offline!

---

### Post by pennygov on 2008-11-19
Thanks! I just spent an hour trying to edit my config files which was rather confusing since the setup was nothing like the old way. Dah ... so simple!  ;-)

---

### Post by ghotighongers on 2009-05-06
Thanks, you just saved me so much trouble... :)

*kudos*

---

### Post by binbash on 2009-05-09
Thanks

---

### Post by joemun on 2009-05-28
Artha is a dictionary like wordweb on windows, for linux download de deb packages and just double click.IMHO it is the best dictionary for linux so far.
 [http://artha.sourceforge.net](http://artha.sourceforge.net).

---

### Post by binbash on 2009-05-28
> **joemun said:**
> Artha is a dictionary like wordweb on windows, for linux download de deb packages and just double click.IMHO it is the best dictionary for linux so far.
 [http://artha.sourceforge.net](http://artha.sourceforge.net).

It depends on tcl tk which just suck :/

---

### Post by kickwin on 2009-05-29
I concur joemun. Artha kicks ###.

---

### Post by Noobs*McGee on 2009-05-29
I can't get this to work for me :(

I followed the instructions to the letter: installed the dictd and dict-gcide packages via synaptic, opened Dictionary from the apps menu, added the new source with localhost in the hostname, made sure the new source was selected, and tried to look up a word, but every time I try, I get the error "Connection failed to the dictionary server at localhost:2628"...

I'm a fairly recent convert from WinXP, and I'm not particularly Linux saavy, so I apologize if I'm making a stupid mistake and the solution is very obvious, but I'd appreciate any help you can give...

---

### Post by Noobs*McGee on 2009-05-30
Help?

---

### Post by legends2k on 2009-06-01
**@Noobs*McGee**:
You can try this:
[http://ubuntuforums.org/showthread.php?t=1065384](http://ubuntuforums.org/showthread.php?t=1065384)

---

### Post by jon.reeve on 2009-06-01
Noobs*McGee: Try changing your hostname from localhost to 127.0.0.1 and see if that works. Let me know if that solves the problem and I'll revise the original post. I had trouble too after upgrading to jaunty.

---

### Post by timetunnel on 2009-06-03
> Try changing your hostname from localhost to 127.0.0.1 and see if that works

I had the same problem and switching from localhost to 127.0.0.1 solved it for me (on Jaunty)

---

### Post by Noobs*McGee on 2009-06-04
Hey, sorry it took me so long to respond, I haven't been online in a few days.

jon.reeve, your suggestion to switch the host name to 127.0.0.1 seems to have done the trick, it works great now.  Thanks a ton for your help :D

---

### Post by kgaipal on 2009-07-08
that realy helped ... thnx :D:)

---

### Post by Gnatcho on 2009-07-17
Thanks for the howto.  It was very easy to implement.

How would I go about making it so that it searches all available dictionaries?  Dict.org seems to have the meta-file "All Dictionaries (English-only and English-translating)" for this purpose and that's really all I need.

---

### Post by nomnex on 2009-09-25
I don't like StarDict too. It is resource full, but I find it messy. But what does really matter, the functions or the content? If we are talking about a dictionary, it is definitively the content.
With StarDict, you can use most of the Babylon Dictionaries O-O-B (for free). They are on SourceForge on the download page. You will only have to convert them, from the Babylon website, if you are looking for the last edition or some missing dictionaries.

Agreed, the GNOME-Dic, and now Fantasdic have a nice GUI and they are easier to use (a big minus for a missing scan function). This thread, and another before this one, explains how to use local dictionaries, even though, initially these are on-line tools (especially Fantasdic with Jap. dic.). But if you do any serious job with a dictionary off-line, you are (sadly?) back to the source with "StarDict" unless someone comes with a tool to convert Babylon files in other formats? Fantastic has the project to implement StarDict format. That could be a solution, but that's not done yet.

---

### Post by sopadeajo on 2009-10-01
> **jon.reeve said:**
> 

```

sudo apt-get install dict-moby-thesaurus
```Now to configure Dictionary, open the Dictionary program (in <Hardy it's in Accessories, in Intrepid it's under Office), go into Edit -> Preferences, click on "Add" to add a source, then under "Description" give it a name like "Local Dictionaries," under "hostname" type "localhost" [EDIT: In Jaunty and later you might try putting "127.0.0.1" (without the quotes) instead; see below] and leave the port number the same. Now click "add" and now whenever you're offline you can choose "Local Dictionaries" from "Dictionary Sources" and access your dictionaries offline!

OK; thanks, but this does not explain if we want to have 2 or more dictionaries.It seems that there is no way to install more than one and let the program know which one to select...

---

### Post by jon.reeve on 2009-10-02
> **sopadeajo said:**
> OK; thanks, but this does not explain if we want to have 2 or more dictionaries.It seems that there is no way to install more than one and let the program know which one to select...

What problems are you having with installing more than one dictionary? For me, it's as simple as installing more dictionary packages. For example, I installed the Collaborative English Dictionary, a French-English dictionary and an English-French dictionary this way: 

```
sudo apt-get install dict-gcide dict-freedict-fra-eng dict-freedict-eng-fra 

```

And I can install as many as I want. Now the Dictionary application lists several dictionaries under "available dictionaries."

---

### Post by psifunk on 2009-11-06
Hello. I want to install a greek-english dictionary but there is no such thing in the repos. Is it posible to find it from another source and install it under ubuntu or should it be already prepared in some sort of way. Cheers

---

### Post by sitthykun on 2010-06-24
sudo apt-get install dict-gcide dict-freedict-fra-eng dict-freedict-eng-fra

I already update but I cannot find the application

Can you help me, please?

:guitar:

---

### Post by wkhasintha on 2010-06-26
Thanx for the info sir

---

### Post by jon.reeve on 2010-06-30
> **sitthykun said:**
> 
I already update but I cannot find the application


What application?

---

### Post by lover88 on 2010-08-15
Thanks dude!!!!! u saved my time

---

### Post by sn0m on 2011-09-26
thanx guys, this artha thing should be installed by default in ubuntu, imo.

---

### Post by mungatsuma on 2012-06-12
> **jon.reeve said:**
> I searched all over to find an offline dictionary solution to meet my needs, since I'm often in need of a dictionary and thesaurus I can use offline. Having not found an adequate solution in OpenDict (its dictionaries are only for foreign languages like Latvian and its website is inundated with spam), Stardict (it's bloated, written in bad English, and generally annoying to use) or other programs, and not always having access to the internet whenever I need a dictionary, I figured out how to set up a local DICT server and thereby use the Dictionary program that's already included with Ubuntu to access locally stored dictionaries. It's not all that difficult, it turns out. 

First, install DictD: 

```
sudo apt-get install dictd

```this installs a DICT server. now you can install whatever dictionaries you want. Dictionaries are in the repos, here's a list I found using a package search: 

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=dict](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=dict)

so to install a thesaurus, for example, use
```

sudo apt-get install dict-moby-thesaurus
```Now to configure Dictionary, open the Dictionary program (in <Hardy it's in Accessories, in Intrepid it's under Office), go into Edit -> Preferences, click on "Add" to add a source, then under "Description" give it a name like "Local Dictionaries," under "hostname" type "localhost" [EDIT: In Jaunty and later you might try putting "127.0.0.1" (without the quotes) instead; see below] and leave the port number the same. Now click "add" and now whenever you're offline you can choose "Local Dictionaries" from "Dictionary Sources" and access your dictionaries offline!

The above configuration with localhost still works in Ubuntu Precise.

Thanks for the tip.

---

