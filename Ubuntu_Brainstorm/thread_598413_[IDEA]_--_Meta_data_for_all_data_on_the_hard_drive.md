---
title: "[IDEA] -- Meta data for all data on the hard drive"
date: 2007-10-31
forum: Ubuntu Brainstorm
---

### Post by altonbr on 2007-10-31
(Probably for Hardy + 4)

I know Microsoft worked on this for Vista and said that it was too advanced to implement so early, but if we can start using Nautilus (or at a lower level, ext4) to save meta data for people's /home partitions, then you'd be able to find documents MUCH easier.

This is reminiscent of "Web 2.0"s tag cloud format where a SQL DB has thousands of keyword associations that link to different pictures, documents, etc.

Currently I have to name my folders something like:

/home/brett/my_photos/20071031-birtday_party/
or
/home/brett/my_documents/journal/20071031-nature_and_its_warmth.odt

just to give my documents some relevant data. Yes, there is a 'date modified' and 'date created' column but those dates don't always gets copied over when movies data from HD to HD to Flash drive through MSN Messenger and so on.

So what if I wanted to tag my ODT document with "flower, sun, warmth, photosynthesis" etc. and then names of the people I mention in the document such as "David Suzuki, Thomas Homer Dixon"? I'd have to put it in the name of the document. Would it not make more sense to give associative data to documents?

What's the current technical implementation of this? And who is/will be working on it? The kernel developers with ext4 or Gnome for 2.22/2.24?

What do you think?

---

### Post by 23meg on 2007-10-31
You can already do this in Gutsy thanks to Meta Tracker, but the DE integration work isn't done yet.

---

### Post by altonbr on 2007-10-31
Yeah I see that, but it still needs MUCH better integration with Nautilus where you can right-click or when you have a file selected, add a 'tag' in the information pane to the left.

I still don't know how to add meta data with Tracker.

---

### Post by 23meg on 2007-10-31
> **altonbr]Yeah I see that, but it still needs MUCH better integration with Nautilus where you can right-click or when you have a file selected, add a 'tag' in the information pane to the left.[/QUOTE]

I think there's a nautilus-python extension that implements this, as well as a Meta Tracker awareness patches for Nautilus, and there may be code in Nautilus SVN that does it too said:**
> I still don't know how to add meta data with Tracker.

For now, you can add metadata via tracker-search-tool, via the command line, with the extension I mentioned, or with hacks such as [this]("http://ubuntuforums.org/showthread.php?t=520845").

---

### Post by altonbr on 2007-10-31
Great information 23meg, but since it's still not fully integrated in Nautilus, I'll make a blueprint and see what the developers think.

I'll probably have more success with GNOME and bugzilla, so I'll try both.

Thanks again.

---

### Post by altonbr on 2007-11-13
> **altonbr said:**
> Great information 23meg, but since it's still not fully integrated in Nautilus, I'll make a blueprint and see what the developers think.

I'll probably have more success with GNOME and bugzilla, so I'll try both.

Thanks again.

It looks like someone agrees with me: "We're only Human after all: a review of Ubuntu 7.10 Gutsy Gibbon"
[QUOTE=http://arstechnica.com/reviews/os/ubuntu-gutsy-gibbon-review.ars/5]Tracker needs a better dedicated search tool with support for more sophisticated filtering and sorting. Better integration of Tracker tagging and metadata features is also required in order for users to be able to use Tracker to its full potential. Ideally, users should be able to associate tags with files directly through the file manager.[/QUOTE]

---

### Post by 23meg on 2007-11-30
Here's [Scott James Remnant]("https://launchpad.net/~keybuk") on metadata integration in desktop apps:

[http://www.netsplit.com/2007/11/30/on-metadata/](http://www.netsplit.com/2007/11/30/on-metadata/)

We really need to make this stuff happen.

---

### Post by altonbr on 2007-12-01
> **23meg said:**
> Here's [Scott James Remnant]("https://launchpad.net/~keybuk") on metadata integration in desktop apps:

[http://www.netsplit.com/2007/11/30/on-metadata/](http://www.netsplit.com/2007/11/30/on-metadata/)

We really need to make this stuff happen.

Thanks 23meg, I made a post on his blog. I appreciate your efforts in helping.

---

### Post by atlfalcons866 on 2007-12-07
everything is stored as metadata on ntfs if that matters

---

### Post by altonbr on 2007-12-08
> **atlfalcons866 said:**
> everything is stored as metadata on ntfs if that matters

As it is with EXT3. But the problem is, there aren't enough 'tags' to really organize the data, so we're stuck with very descriptive names on the files.

Even so, like I said with the date, yes, the date created is stored as metadata but if you move it to a foreign file system, that metadata gets erased which is a huge problem.

Interopitability of metadata will be Linux vs. Windows vs. Mac's greatest challenge.

---

### Post by puccaso on 2007-12-09
i want everyone to read something on the tracker website :
> ** Use Cases **

 [LIST]
[*] Application-neutral and desktop-neutral tagging. Tagging support 'for free' in any application that uses Tracker, such as Nautilus and file-chooser dialogs.
[*] A cross-application metadata database. If applications chooses to use Tracker as their metadata database and indexer, they would see signifigant improvements. Users would no longer need to add a MP3 they have downloaded to Rhythmbox, nor a photo they have taken to f-spot, these items would be detected and imported automatically.
[*] Users may completely move away from a folder-heirarchy based home folder, and instead organise their data into collections using tags. The combination of tagging support in the file-chooser, tagging awareness in Nautilus, or even a tag based filesystem using FUSE could allow radical exploration of new desktop ideas.
[*] Improved performance. With an always running indexer, application start-up time could be dramatically reduced in instances where applicaions scan or parse a numer of files on disk. For example, Alacarte could use it as its desktop file parser, or Rhythmbox as its song index. In addition, by using a DBus-based API, one can take advantage of asynchronous replies for improved GUI responsiveness.[/LIST]


why has none of this been done?

but seriously imagine - rhythmbox just finding music on the whole system based on the index.. 

and the home directory not being hierarchical - just being based on context - like an object oriented filemanager rather then a file oriented one. 

linux does a good job in not needing file extensions anyway so why not go a step further?


i think the hardy devs could AT LEAST port the old nautirlus-tracker dep into nautilus for hardy!!!!

---

### Post by 23meg on 2007-12-09
I've merged this into the relevant thread. Those steps will be taken, but they require upstream work. I don't think we'll ever see Nautilus get Tracker support in Ubuntu without it happening upstream.

---

### Post by coolen on 2007-12-09
I think the reason this hasn't happened yet is that, first, it's a work in progress. These seem more like goals than current functionality.
Additionally, if a program is made to use Tracker, the devs must be fairly confident that it will always find Tracker on any system it's installed on. I've only started hearing about Tracker over the past six months or so. Granted, I'm not really up to speed on FOSS developments, but it still all seems rather new.

---

### Post by puccaso on 2007-12-09
well i undestand what you are saying
but most ubuntu installations come installed with uxterm or xterm - but no one uses them
all the devs have to do is make sure that tracker is a dep for nautilus and hey presto. 

even so - there are like 5 different methods of searching for something, find files in nautilus - tracker - beagle - search for files inthe places menu - this is stupid.

the ubuntu team just have to make a stand.

---

### Post by coolen on 2007-12-09
True, but the devs aren't catering simply to Ubuntu. Just because Ubuntu uses Tracker, doesn't mean all of the other distros do.
It's all very new, and it'll take a while to figure everything out. A lot can be done with this technology, and it'll be great once everyone figures out how to incorporate it into their code, but it won't happen all at once. A few starter projects will crop up, some DE integration work will be done, then a few features will start appearing in your existing applications. Eventually you'll have full advantage being taken of Tracker, but it's a slow process.

---

### Post by 23meg on 2007-12-09
[QUOTE=coolen]Additionally, if a program is made to use Tracker, the devs must be fairly confident that it will always find Tracker on any system it's installed on.[/QUOTE]

Which has to do with Tracker being included in GNOME, and having reliable fallback mechanisms for cases where it's not installed.

[QUOTE=pucasso]all the devs have to do is make sure that tracker is a dep for nautilus and hey presto. [/QUOTE]

Not really. Tracker *is* already a dependency of Nautilus, but that doesn't mean Nautilus integration is done, let alone meaning the rest of the desktop integration is done. A lot of the Tracker related functionality implemented in Nautilus via extensions and patches still hasn't been integrated into trunk, thus didn't make it into release versions. 

[QUOTE=pucasso]even so - there are like 5 different methods of searching for something, find files in nautilus - tracker - beagle - search for files inthe places menu - this is stupid.[/QUOTE]

Searching in Nautilus uses Tracker, and Beagle isn't installed by default. In any case, context searches in Nautilus aren't redundant with "Places / Search for Files".

[QUOTE=pucasso]the ubuntu team just have to make a stand.[/QUOTE]

And ship Nautilus and other default apps with immature patches in a LTS release? No thanks; it's best to wait for (and help, and keep in close contact with) upstream.

---

### Post by altonbr on 2007-12-10
This is exactly why I stated "Hardy + 4". What I expect LTSes to do is to take all of the new technology that the devs have been playing with over the past 3 releases and iron them out for greater stability.

I expect this to begin in Hardy + 1 and be closer to finalized in Hardy + 4 when Vista SP2 or Mac OS X 10.7 are out and possibility displaying similar technology.

If anyone forgets, this was supposed to be implemented at the file-system level for Vista, but the M$ devs stated it was too experimental and we should wait for Vista + 1 (which is dubbed Windows 7, am I correct?).

Thus we're looking at 10.04 LTS to implement the "no file-system, everything is tagged" concept. Possibly along with ext4 or a file-system that can store tags of all sorts instead of the holding the information in a database at the software level [Tracker].

---

### Post by puccaso on 2007-12-10
+1 i like the responce. positive and yet not so explosive. i like it.

---

### Post by 23meg on 2007-12-12
I don't think the hierarchical base structure is going anywhere so soon as Hardy+4. I'm talking about userspace abstractions and metadata awareness in desktop apps. 

 I don't know of any widely accepted arguments for the usefulness of filesystem-level metadata for anything outside the scope of high level desktop apps, which it seems can do just as well with userspace solutions, if not better.

---

