---
title: "Document Management application"
date: 2006-01-24
forum: Server Platforms
---

### Post by jasont.t on 2006-01-24
Hi,
 I hope someone can help. I'm looking at setting up a document management Ubuntu/debain server; however I don't know what application I should use or be looking at. Can anyone make some suggestions?

Note, the sorts of requirements I'm after are:

- 90% of users are on Windows, so I'm probably looking for a Web based solution.
- Currently there will be about 10 users however it will likely increase to 50 or so.
- Easy (or relatively) to manage.
- Documents would generally be in MS office stuff (xls, doc, etc..)
- Version Control would be great.

Thanks

---

### Post by nesman89 on 2006-01-24
Have you thought about using a Wiki.  it is a great central repository where everyone can add comments, and does version control on the pretty much all files.  i'm currently using projectforum because it's self contained(no setting up apache, perel,etc) however is does cost a little bit.  there are a lot of free wiki's on the web that would probably meet your needs.

---

### Post by nesman89 on 2006-01-24
Have you thought about using a Wiki.  it is a great central repository where everyone can add comments, and does version control on the pretty much all files.  i'm currently using projectforum because it's self contained(no setting up apache, perel,etc) however is does cost a little bit.  there are a lot of free wiki's on the web that would probably meet your needs.

---

### Post by zkissane on 2006-01-24
[QUOTE=jasont.t]Hi,
 I hope someone can help. I'm looking at setting up a document management Ubuntu/debain server; however I don't know what application I should use or be looking at. Can anyone make some suggestions?

Note, the sorts of requirements I'm after are:

- 90% of users are on Windows, so I'm probably looking for a Web based solution.
- Currently there will be about 10 users however it will likely increase to 50 or so.
- Easy (or relatively) to manage.
- Documents would generally be in MS office stuff (xls, doc, etc..)
- Version Control would be great.

Thanks[/QUOTE]

Subversion.

subversion.tigris.org

The package name on apt is subversion.  Read the documentation [here](http://svnbook.red-bean.com/).  For the Windows client side, there's [Tortoise Subversion](http://tortoisesvn.tigris.org/).  It integrates very nicely into the Windows shell.

---

### Post by jasont.t on 2006-01-24
Thanks for your feedback. I didn't think of a wiki, that might be the way to go, however I'll have a look at both.

---

### Post by xerophyte on 2006-01-27
You might need to take look at the: 

1) Trac : which has svn and wiki intergrated [http://projects.edgewall.com/trac/](http://projects.edgewall.com/trac/)

2) you can take look at plone too [www.plone.org](www.plone.org) 
plone allow you to create all kind of content include ms file and stuff and you can search them and has verion control too 

hope that helps

---

### Post by jasont.t on 2006-01-27
Thanks xerophyte, however I think I found what I'm after, DocMan.

[http://www.mambodocman.com/](http://www.mambodocman.com/)

---

### Post by hillsy on 2006-01-28
Knowledge Tree is also pretty good:

[www.ktdms.com](www.ktdms.com)

---

