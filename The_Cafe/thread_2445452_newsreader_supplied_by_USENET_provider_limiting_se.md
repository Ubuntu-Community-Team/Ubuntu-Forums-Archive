---
title: "newsreader supplied by USENET provider limiting search results?"
date: 2020-06-14
forum: The Cafe
---

### Post by AnotherBrian on 2020-06-14
I'm able to access some old articles which cannot be found by using a usenet  provider's newsreader.  This makes me think that they are not making the entire newsfeed visible via their newsreader.  

Is this so?  

Related on this is the overall design of their service and their newsreader. 

I'm guessing their client newsreader interfaces with a backend search engine on the provider's servers.  Thus, the info made visible by the backend search engine limits what is visible via their client newsreader. While this may provide very fast access to search results, its disappointing if only a bit of what is out there is accessible.  

in the old days this is how a newsreader worked.  First, for the newsgroup of interest, the article headers had to be downloaded. Once those were on the client machine, the selected  individual articles could be downloaded.  
the header files could be huge both in storage volume and time to download and so for example fetched headers could be limited to a date range or since last fetched.  
The behavior of the usenet provider's newsreader suggest they are not downloading the header files into the client machine. 

Any suggestions on a good newsreader to  use which would bypass the usenet provider newreaders limitations or maybe it is just a usage issue on my part?   Klibido use to be a preferred binaries downloader but requires a build by the user these days. I don't know if there are any issues to getting it to work.

---

### Post by MoebusNet on 2020-06-27
Have you tried: [https://binsearch.info/](https://binsearch.info/) ?

Free web-based search engine; monthly fee for advanced features like no-longer-current articles. Might be worth a look.

---

### Post by AnotherBrian on 2020-08-16
I think I figured it out.   I'm thinking that the USENET provided reader screens material perceived as copyrighted.   They didn't say this outright but that is the impression I got.  

Another possibly is their backend search engine may not be picking up all the content.  The design must be something like they have a database mapping search terms to header ids.  In background mode they have to construct the database and then add to the database over time as new articles come in. Any of that may get corrupted and then it would be a large effort to rescan all that content.  Also they would need audits to assure to detect something is broken. 

Some of the features on the provider's newreader are nice such as taking a peek at content before downloading a large file.

I don't consider sabnzb as a USENET reader. It  requires an nzb indexer and a significant amount of content is not based on nzb.  

pan chokes on large sets of header files.    klibido I don't think will run on ubuntu but perhaps on kubuntu.  Not sure on this.  

Are there any good newsreaders out there for linux?  

Thank you for the suggestion about binsearch.info.

---

### Post by sdsurfer on 2020-08-17
There is also the Wayback Machine, the internet archive but not sure if it archives news feeds.

---

### Post by AnotherBrian on 2020-09-12
I ended up finding another newsreader,  **_newsflash plus by ensisoft_**.  
This newsreader is header file based meaning header files need to be downloaded before the individual articles can be read.  
So it is like pan in this regard.  It also is able to handle the large files found on usenet like rar files etc and unpack them.  

where pan goes into high cpu usage when the number of downloaded header files is large, newsflash can handle it. 

the newsreader supplied by _newshosting_, although is has  nice preview features, the backend search function appears to greatly restrict_ the viewing of huge amounts of usenet_.  

I also subscribed to eweka to do some experiments between the two platforms (eweka and newshosting).  I did full downloads of all available header files  in several newsgroups using _newsflash_.  it appeared to me that both eweka and newshosting have identical headerfiles in the several newsgroups. 

That suggests that _eweka_ (who advertises a greater retention period) and _newshosting_ (who advertises a lesser retention period) are are providing identical retention periods and possibly using a common source for usenet content. If that is indeed the case, then there is _no advantage between the two from a retention perspective_ that I can see.

---

