---
title: "Document Collaboration Software"
date: 2009-12-23
forum: Server Platforms
---

### Post by sipickles on 2009-12-23
Hello,

We are a geographically diverse team of software developers working on a project, and in need of document collaboration.

We are keen to have a client/server solution, with the server running on our own Ubuntu server (as opposed to a web based solution)

We are already using trac/svn, but need a useful tool to help share documents and diagrams.

Does Ubuntu have anything to offer on this front?

Thanks

Si

---

### Post by hessiess on 2009-12-23
Not aware of anything spasifically, but couldn't you just use your SVN repo and something like LaTeX for the documents?

---

### Post by sipickles on 2009-12-23
Thanks for the idea.

Was kinda hoping for something a bit more WYSIWYG.

I guess even Office has markup....

---

### Post by hessiess on 2009-12-23
> **sipickles said:**
> Thanks for the idea.

Was kinda hoping for something a bit more WYSIWYG.

I guess even Office has markup....

MS office .doc files and ODF* documents are basically binary files, it is imposable to diff two binary files and get anything usable as a result. Which is why plain text mark-up languages like *TeX or (maby) HTML would be the only option.

Anyway, LaTeX generally produces much better looking documents, with a fraction of the work:)

* ODF is a tarball of XML files, so it would technically be possible to diff them, but as far as I know there are no implementations of this.

---

### Post by sipickles on 2009-12-23
LaTeX isn't really collaborative is it?

It seems to me to be simply a consistent style mechanism

---

### Post by hessiess on 2009-12-23
> **sipickles said:**
> LaTeX isn't really collaborative is it?

It seems to me to be simply a consistent style mechanism

Its a document mark-up language, basically the same principle as HTML, with a different syntax. It can
be used collaboratively when combined with a version control system. Google gives lots of results:

[http://www.google.co.uk/search?q=latex+colaberation&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=latex+colaberation&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by Jekshadow on 2009-12-23
> **hessiess said:**
> MS office .doc files and ODF* documents are basically binary files, it is imposable to diff two binary files and get anything usable as a result. Which is why plain text mark-up languages like *TeX or (maby) HTML would be the only option.

Anyway, LaTeX generally produces much better looking documents, with a fraction of the work:)

* ODF is a tarball of XML files, so it would technically be possible to diff them, but as far as I know there are no implementations of this.

It is possible to diff binaries, Google Chrome uses that for its updates, as all the update server sends is a diff. Here is an example of a binary diff tool: [http://www.daemonology.net/bsdiff/](http://www.daemonology.net/bsdiff/). Something easier to use than *TeX, may be RDF. it is supported on all platforms and you can edit RDFs using MS Word and OpenOffice. RDF is XML, so it can be diffed using normal tools.

---

### Post by volkswagner on 2009-12-24
I know you don't want web based, but in my opinion a wiki is the right tool for the job.

I like [FosWiki]("http://foswiki.org/"), but a great place to start is [WikiMatrix]("http://www.wikimatrix.org/") to choose the one that best meets your needs, using the [wizard]("http://www.wikimatrix.org/wizard.php").

I prefer to download and install in the directory of my choice, vs. apt-get, as this way creating a vhost and removing when no longer needed is easy.

---

### Post by sipickles on 2009-12-24
I don't mind web based as long as we can serve the wiki ourselves.

I guess even trac's wiki could work

---

### Post by volkswagner on 2009-12-24
TracWiki is an interesting choice.  Two things I did notice, it is beta, and does not have WYSIWYG.

I like that it can run it's own web server (self contained).

---

### Post by spynappels on 2010-05-26
For pure document sharing and collaboration, you should also have a look at Alfresco Community edition.

---

### Post by doogy2004 on 2011-02-04
Here are a couple things to check out:

Feng Office (formerly OpenGoo) - [http://www.fengoffice.com](http://www.fengoffice.com)
eyeOS - [http://www.eyeos.org/](http://www.eyeos.org/)

---

### Post by Thirtysixway on 2011-02-04
eyeos is an interesting project, seems a bit overkill for just document sharing.

I like the idea of a wiki, it's simple and clean. And with most wiki software, you can get a plugin to do wysiwyg editing. I personally like mediawiki, but it's up to you.

---

### Post by ubuntu27 on 2011-02-04
Colaborative editor already exist for Linux.

You can use [Gobby]("http://gobby.0x539.de/trac/") for GNOME (Ubuntu)
or use [Kobby]("http://kobby.greghaynes.net/") for KDE (Kubuntu)

Both are in the repository.

---

### Post by HermanAB on 2011-02-05
Abbyword and Knowledgetree.

---

