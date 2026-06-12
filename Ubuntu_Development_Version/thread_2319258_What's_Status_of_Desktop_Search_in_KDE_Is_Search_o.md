---
title: "What's Status of Desktop Search in KDE? Is Search of Kmail Messages Working Yet?"
date: 2016-04-02
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2016-04-02
Anyone know that status of desktop search in KDE on 16.04?  What's working and what is not?

I've been running Kubuntu 16.04.  It's good. However, a search via Krunner does not return Kmail messages.  For a very long time, this was a known problem.  It's my impression that it's been fixed. Has it?  Displaying Folder_Properties->Maintenance in Kmail shows full text indexing is enabled, but the status remains "Still Not Indexed".  I've restarted the indexer several times.

Also, "balooctl status", which returns "the status of the indexer", shows this:
> 
Baloo File Indexer is running
Indexer state: Indexing file content
Indexed 16 / 16 files

Why just 16 indexed files on a system that's been up for days?  

Finally, is searching Kmail messages a "Plasma Search" function or is it a "File Search" function?  Those are the alternatives displayed in System_Settings->Search.  I've never found a lucid explanation of the differences and what does what. E.g., what does the "Terminate Applications" Plasma search plugin actually do?  Does it index apps I have terminated and return them in a Krunner search?

Or are those simply the various little functions Krunner provides, and really have noting at all to do with desktop indexing and searching?

---

### Post by TheFu on 2016-04-02
Don't know about 16.04 - it hasn't been released.  I suspect the search indexer needs to be told where to index and search. Look for some settings. [https://userbase.kde.org/Nepomuk#Indexing_files](https://userbase.kde.org/Nepomuk#Indexing_files) says to specify where to search.  Didn't see anything about updating the indexes.



[B]Why do we need both Akonadi and Semantic Search? Aren't they doing the same thing?
[/B]> 
    In short, Akonadi provides a cache of PIM data like calendar items, contacts and email, which is used by applications like KMail and Korganizer but also the calendar build in Plasma. Semantic Search plugs in Akonadi to provide search functionality. How Baloo offers search is actually up to the application. In case of KDE PIM, Xapian is used to provide indexing and search.

Recoll is another alternative, but doesn't integrate into KDE.  [https://askubuntu.com/questions/688945/is-there-a-way-to-search-document-contents-using-a-unity-lens-in-14-04-trusty](https://askubuntu.com/questions/688945/is-there-a-way-to-search-document-contents-using-a-unity-lens-in-14-04-trusty) It is like a personal google for your connected storage.  Definitely sees inside email files, IME.

I don't run it on my desktops any more, because the indexes can get large and Zimbra has an amazing search [https://blog.zimbra.com/2007/05/the-power-of-search-part-1-the-search-bar/](https://blog.zimbra.com/2007/05/the-power-of-search-part-1-the-search-bar/) facility built-in, but Recoll is amazing too.  I really need to put Recoll on a few storage servers and drop some scripts that run queries in parallel across all systems to be able to find stuff quickly.  Already have a filename-based search that does this, but it could be better.

Recoll has a GUI, but I prefer the CLI interface. I can type 100x faster than I can wait for a GUI and tab between fields.

---

### Post by SeijiSensei on 2016-04-02
I've used Mozilla Thunderbird on my KDE systems for years.  It has an excellent search facility.

---

### Post by buzzingrobot on 2016-04-03
I've used Recoll in the past and it's fine.  As is Thunderbird's internal search, but that's not integrated with the desktop. 

Searching with KRunner will return a list of hits from the search engine's index. This used to include hits on Kmail messages. That went missing during the transition to Plasma 5. A patch to bring it back was accepted about 5 months ago. Hence, my question.

Full desktop search, for people who want it, is a distinguishing feature of KDE. The absence of KMail in that mix make it less attractive.

in this instance, the mail folders are set for indexing and the indexer is running, but the folders are not being indexed.

Nepomuk has been replaced by Baloo.

---

