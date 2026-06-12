---
title: "Subversion noob trying to get one working."
date: 2011-12-25
forum: Server Platforms
---

### Post by pepsifx357 on 2011-12-25
I went by the Ubuntu help site on getting a subversion server running with the https protocol.

The SSL part of the apache2 went fine and seems to be working.

I also installed RapidSVN as my frontend.

When I go to import the repository in RapidSVN, here is what I used.

Repository Url:  [https://localhost](https://localhost)
path:            /home/ben/projects/dubber

The dubber folder was created using the "svnadmin create" command and the config file was edited to include my users and their passwords.

"Recursive" and "Path Type 'Tree" was checked.

When I hit ok, I get this:

```
Error: Error while performing action: OPTIONS of 'https://localhost': 200 OK (https://localhost)
```

I don't know enough about SVN to understand what this even means.  Anyone know how to fix this?

Edit:

I also added this to my /etc/apache2/sites-available/default in the <VitualHost> tag.
```

<Location /svn>
DAV svn
SVNPATH /home/projects/dubber
AuthType Basic
AuthName "dubber"
AuthUserFile /etc/subversion/passwd
Require valid-user
</Location>

```

---

### Post by rubylaser on 2011-12-25
Not really what you're trying to do, but since you're not an svn expert, I thought I'd give you my option. I used to use Subversion for all of my development.  Over the last two years, I've switched entirely over to Git.  Merges are a breeze, and I love the single .git folder rather than all of the .svn files that get scattered across your application.

Setting up a repo is [dead simple]("http://www.alistapart.com/articles/get-started-with-git/") for local development and Github makes team development just as easy.

---

### Post by pepsifx357 on 2011-12-26
> **rubylaser said:**
> Not really what you're trying to do, but since you're not an svn expert, I thought I'd give you my option. I used to use Subversion for all of my development.  Over the last two years, I've switched entirely over to Git.  Merges are a breeze, and I love the single .git folder rather than all of the .svn files that get scattered across your application.

Setting up a repo is [dead simple]("http://www.alistapart.com/articles/get-started-with-git/") for local development and Github makes team development just as easy.

Hey, I'm down for suggestions.  SVN just seemed to be what I was looking for.  I really didn't know what git did.

I have a Music Production company that is in need of some kind of collaboration between three producers in three separate locations.  Each project is passed back and forth until we end up with something we like.  Right now we're using dropbox.com and I just don't feel the security there.  These days you gotta worry about people and companies wrongfully accusing you of copyright infringement so I would like a server to ourselves so we don't have to worry about it.

EDIT:  OMG...I just tried to set one up.  lol  EPIC FAIL on my part.  This is one complicated setup, just from reading the ubuntu community files.  I watched the video of Linus talking about GIT and I like the distributed model, but my understanding only goes so far.  I'm trying to set this up on my machine which contains the core files of the project.  I get lost when it comes to setting up keys and authorization.  I really don't know where this is going when I'm setting it up.  Is there an easier tutorial?

---

### Post by rubylaser on 2011-12-26
Do you have a static ip on your machine?  The first thing you're going to need to have working is either a static public ip or dynamic DNS setup.  Then, you're going to need to port forward port 22 (SSH or move to a non-standard port) to your box for GIT.

Unfortunately, rolling your own shared version control systems aren't as easy to setup as a local repo, and you'll still need to learn how to use whatever tool you choose.  Here are some decent directions to [setup git]("http://tumblr.intranation.com/post/766290565/how-set-up-your-own-private-git-server-linux").

Or use [Gitolite]("http://www.silassewell.com/blog/2011/01/08/setup-gitolite-on-ubuntu/").

---

