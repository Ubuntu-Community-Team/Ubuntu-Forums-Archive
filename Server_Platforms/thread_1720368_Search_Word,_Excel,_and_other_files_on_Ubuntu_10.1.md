---
title: "Search Word, Excel, and other files on Ubuntu 10.10 Server with web-based interface"
date: 2011-04-03
forum: Server Platforms
---

### Post by kyutums on 2011-04-03
I have Ubuntu 10.10 (2.6.35-28-generic) on a headless server. I would want to use it as a searchable file server to house the various documents we have at home.

I'm already using Samba on it to accept the files from various computers at home. However, I would want a web-based interface to search inside the documents in specific folders.

I have just installed the solr-tomcat package (sudo apt-get install solr-tomcat). I tried accessing the web interface via [http://192.168.1.28:8983/solr/admin/](http://192.168.1.28:8983/solr/admin/) (got this tip from [http://wiki.apache.org/solr/SolrAdminGUI](http://wiki.apache.org/solr/SolrAdminGUI)), but Firefox can't establish a connection to the server.

I have Apache 2 and PHP running on it and I'm not sure if this is causing any conflict with the solr-tomcat package.

I'm a newbie when it comes to Solr (or anything Java for that matter) and would rather install things on Ubuntu via apt-get (for a clean uninstall of stuff if needed). Any tips on how to get this going would be very much appreciated. :)

---

### Post by TwiceOver on 2011-04-03
I've been looking for this for a LONG time.  I got SOLR running, but at the time you had to actually manually archive each document.  Don't know if that has changed.

Anyway...  Wanted to mark this thread to see how it goes for you.  I used to use Google Desktop with a proxy front end and that worked great, but Google closed that hole...

---

### Post by kyutums on 2011-04-20
I went the Google Desktop route too for a while (it solved the issue for the Windows machine), but I work on a Mac too. :( Also, working with a common interface would be best. :)

---

### Post by mande01 on 2011-05-07
Hey, how's it going?

I too am real keen on how this goes.
Could some one point me to the version of GDS that allowed the proxy to work?

Good luck,
I hope my little bump will get you more attention.
What search software do web site admins use?

Ta,
Derry

---

### Post by SeijiSensei on 2011-05-07
> **mande01 said:**
> What search software do web site admins use?

I still use the venerable [htdig]("http://www.htdig.org") to index some online listserver archives I maintain. It's pretty fast and quite flexible.  You can also have it use external parsers like [catdoc]("http://wagner.pp.ru/~vitus/software/catdoc/") to index Word and Excel files.  It's designed to run on a web server like Apache.  The parser starts from an initial index page and follows all the links it finds.  You can specify rules to constrain what items get indexed.  If you know a bit of HTML and can set up Apache, you can use htdig to build an index of your documents that is accessible from a web interface.

I've also used the remarkable [SphinxSearch]("http://sphinxsearch.org/") to enable customers to search a database of product information.  Sphinx was developed to index documents stored in an SQL database, though, so it's not oriented toward indexing ordinary documents residing in the file system. (There is a way to do it, but it's not simple.)

---

### Post by kyutums on 2011-05-07
> **mande01 said:**
> I too am real keen on how this goes.
Could some one point me to the version of GDS that allowed the proxy to work?

Not too sure on what exact version, but the latest GDS allowed me to search on a remote SMB server. :)

---

### Post by tgalati4 on 2011-05-07
There are several robust document management solutions out there, such as:

[http://bitnami.org/stack/knowledgetree](http://bitnami.org/stack/knowledgetree)

---

### Post by kyutums on 2011-05-08
I tried KT, but installing it with an existing Ubuntu machine was unsuccessful.

---

### Post by Kaput1982 on 2012-03-20
I know this is an old thread, but I've been looking for something similar.  Just a note to the OP the port is 8080.  So  [http://192.168.1.28:8080/solr/admin/](http://192.168.1.28:8080/solr/admin/) should work.

---

