---
title: "SVN repository selection...."
date: 2008-09-30
forum: Server Platforms
---

### Post by chadeto on 2008-09-30
Hello all,

I am a little confused with SVN thing. I am a PHP developer. I am using Dreamweaver as my editor on my WindowsXP machine, and Dreamwever connects directly to my dedicated server which is Ubuntu.

I installed SVN on the server, and verified that it is working. I also installed MyTortoise on my local machine. I am confused on where to select as my repository on the server.

I need to commit my changes to repository, and then copy them to /var/www/ . Am i right? Is there an easy way, or should I select my repository under /var/www/ ?

Thanx for ideas...

---

### Post by Kismet on 2008-09-30
I'm a little confused at the question, but I'll offer my thoughts.

SVN functions as a code repository so you and presumably other people can work on the same code. 

Typically if you want to move up a live project, you check out the latest project from the repository and put it up on your live server.

You could check it out directly to where your webserver(Apache?) is looking for it, or you could just copy your working copy over to the deployment directory.

---

### Post by chadeto on 2008-09-30
I see :) we have a project under development. So we make changes alive as soon as they happen. So, if one of the developers adds something, they upload the file directly to /var/www. Now, I want to switch to SVN so that versioning can be done by SVN. But each time a minor change happens, we need to first commit it to repository, and then export it to /var/www.

I am thinking of this solution: If i install an SVN client to the server, and set this client's working directory to /var/www, requesting SVN client at server to synchronize at each commit.


What do you say?

---

### Post by chadeto on 2008-09-30
I found this :


----------------------------------------------------------------
**I'm managing a website in my repository. How can I make the live site automatically update after every commit?**

This is done all the time, and is easily accomplished by adding a post-commit hook script to your repository. Read about hook scripts in Chapter 5 of the book. The basic idea is to make the "live site" just an ordinary working copy, and then have your post-commit hook script run 'svn update' on it.

In practice, there are a couple of things to watch out for. The server program performing the commit (svnserve or apache) is the same program that will be running the post-commit hook script. That means that this program must have proper permissions to update the working copy. In other words, the working copy must be owned by the same user that svnserve or apache runs as -- or at least the working copy must have appropriate permissions set.

If the server needs to update a working copy that it doesn't own (for example, user joe's ~/public_html/ area), one technique is create a +s binary program to run the update, since Unix won't allow scripts to run +s. Compile a tiny C program:

#include <stddef.h>
#include <stdlib.h>
#include <unistd.h>
int main(void)
{
  execl("/usr/local/bin/svn", "svn", "update", "/home/joe/public_html/",
        (const char *) NULL);
  return(EXIT_FAILURE);
}

... and then chmod +s the binary, and make sure it's owned by user 'joe'. Then in the post-commit hook, add a line to run the binary.

If you have problems getting the hook to work, see "Why aren't my repository hooks working?".

Also, you'll probably want to prevent apache from exporting the .svn/ directories in the live working copy. Add this to your httpd.conf:

# Disallow browsing of Subversion working copy administrative dirs.
<DirectoryMatch "^/.*/\.svn/">
    Order deny,allow
    Deny from all
</DirectoryMatch>

----------------------------------------------------------------

---

### Post by Kismet on 2008-10-01
That seems like a good solution, alternately you could set up a cron job to run svn update in that directory every couple of minutes. :)  ... if you wanted the (IMO) the easiest solution.

We use a java servlet for our webapp, so its all set increments and updates only happen to the live after significant changes. I just check it out into a dummy directory directory on the server, tar it with -exclude .svn and then untar in the deployment directory.

Your solution sounds like it will work very well for a static or interpreted site!

---

