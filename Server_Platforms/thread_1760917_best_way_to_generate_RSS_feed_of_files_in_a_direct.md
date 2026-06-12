---
title: "best way to generate RSS feed of files in a directory structure"
date: 2011-05-17
forum: Server Platforms
---

### Post by SpaceBas on 2011-05-17
Hey folks,
I have a file server that uses various tools to pull new files into a directory structure like this:
/local/media

inside /local/media are lots of directories and sub directories, many with files. 

I'd like to create an RSS feed of new files (and prune old files) and serve that RSS feed to client readers who could then access the files. 

Currently, I create symbolic links to new files in /local/media/New using a find command:

```
find /local/media/TV -mtime -3 -size +1000k -exec bash -c '[[ -L /local/media/New/${1##*/} ]] || ln -s "$1" /local/media/New' _ {} \;
```

I also prune old sym links the same way:
```
find /local/media/New/ -mindepth 1 -mtime +4  -exec /bin/rm -r {} \;
```

So ideally, I'd like to simply make an RSS feed of the files in /local/media/New since it already contains sym links to the files I want and prunes automatically. 

Alternativly, I'd settle for a package which gives me similar flexibility. 

Any suggestions?

---

### Post by Lars Noodén on 2011-05-18
There is [XML::RSS](http://search.cpan.org/~kellan/XML-RSS-1.05/lib/RSS.pm) for perl in CPAN.

---

### Post by SpaceBas on 2011-05-18
Thanks Lars - now...to learn perl :)

---

