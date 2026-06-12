---
title: "Looking for a document repository application."
date: 2011-02-09
forum: Server Platforms
---

### Post by 1clue on 2011-02-09
Hi,

I'm trying to replace an office file server.  I would like to avoid just another samba share.

I'm looking for a document repository, a bit more functionality than a plain samba share and very cross-platform.

I've looked a couple minutes at dspace, but that seems like a lot of work just configuring it.  Dropbox would be fine except that they only have up to 100g, and it's off-site.

This is NOT for unauthenticated public use.

Here are some features I have in mind:


   1. Web front end.
   2. Any file format from a one-line text document to a Microsoft Word document to an ISO of a blu-ray disk to a very large database backup, binary or text.
   3. Cross-platform clients, mostly Mac.
   4. Authenticated via centralized one-login server or maybe by a key such as an SSH public key.
   5. Searchable by terms, name or content if the type is appropriate.
   6. Pass in the URL for an object and have the server download it.
   7. Stores files in native format so if the app breaks I can just get the files.



Anyone have any suggestions for something that's even close to this?

Thanks.

---

### Post by HermanAB on 2011-02-09
Knowledgetree does all that and more.

Get a VM from bitnami.org.

---

### Post by 1clue on 2011-02-09
Thanks, I'll look into it.

---

### Post by SeijiSensei on 2011-02-09
You can set up a WebDAV share with Apache's [mod_dav]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html").  Windows users can mount a DAV share as a folder on their desktops.  You have all of Apache's many authentication mechanisms available as well, plus SSL encryption if you'd like.

I've looked at dspace a couple of times for another client.  It looks so useful, but it does appear to require a lot of effort to get it running.  I've not run Java applications on my webservers, so I'm a little daunted by dspace.

The only thing WebDAV can't give you is the searching tools.  I've written PHP applications that let users post documents and include keywords and other information for searching.  Another option is full-text indexing and searching using something like [htdig]("http://www.htdig.org/").  If you end up storing the documents in a database rather than as files, I'd look into the [Sphinx]("http://sphinxsearch.com/") index.

---

### Post by 1clue on 2011-02-09
One other thing that could give me most of this is a standard samba share and then have an indexing/searching app that sits on top of that.  That way I could offer a standard share for mac, windows and linux and also have an http interface that searches.

Each directory name is a search term, as is the file name, the short file name and the entire path.

We get this thing where the same directory names exist but in different order on the path.  And of course all intended to go to the same place.  I can't stand it.

I don't think anyone here would go for storing binaries like word docs in a database.

One thing that would be great though is a duplicate detection strategy, that's the only reason I can think to use a db.

Thanks, I have some research to do.

---

### Post by SeijiSensei on 2011-02-09
I don't usually put the documents into an SQL database either.  Usually I just place all the files in some directory and have pointers to the documents in the database.  You won't get full-text searching that way, but depending on what characteristics you store in the DB, you can search by title, author, date, keyword, etc.

---

### Post by elico on 2011-02-13
SFTP and aike.
you might want to build the server and use VPN\sslVPN to transfer the files\database in.
so the server will have only SSH AND VPN access and through them get more access using a Virtual network. 
you can also look at TURNKEY LINUX.

---

