---
title: "Setting up private SVN server"
date: 2007-05-23
forum: Server Platforms
---

### Post by Naatan on 2007-05-23
Hi, I am trying to setup a SVN server on edgy...

well actually its already set up, and working, only I cant seem to login to it remotely.

the tutorial I followed ([http://urbanpuddle.com/articles/2006/05/03/setting-up-subversion-on-ubuntu-dapper-drake](http://urbanpuddle.com/articles/2006/05/03/setting-up-subversion-on-ubuntu-dapper-drake)) said that I should do a checkout on the remote client like so:

svn co svn+ssh://foo.com/home/svn/project1/

only that doesnt work (asks for login and even root login doesnt work..), furthermore I dont want the people I give access to the svn server to have access to ssh aswell (duh).

So I want to be able to do a checkout like you would normally do: svn co svn://server.com/svn/project

but when I do that for my host I get:

svn: No repository found in 'svn://host.com/svn/project'

so my question: how do I setup the remote part of my svn server, eg. how do I let users connect using svn:// and have them login with the svn logins I specified in authd and passwd.

Thanks in advance!

---

### Post by pansz on 2007-05-23
> **Naatan said:**
> 
so my question: how do I setup the remote part of my svn server, eg. how do I let users connect using svn:// and have them login with the svn logins I specified in authd and passwd.

Thanks in advance!

svn+ssh do not need a server at all, so it is the easist to set up.

What you need is to set a svn server, see SVN book for that, 
here is a link:

[http://svnbook.red-bean.com/en/1.2/svn.serverconfig.svnserve.html](http://svnbook.red-bean.com/en/1.2/svn.serverconfig.svnserve.html)

---

### Post by SeanHodges on 2007-05-23
The main thing to remember is that the subversion server does not include a network transport mechanism of it's own, it relies on other applications to do this for it (for a number of reasons, including scalability with existing systems)

So, you need to use another tool to make it accessible remotely.

I cant go into details at this point, because you need to decide which method you want to do first.

The way I always opt for is by using the subversion module in Apache. This is a fairly simple process, and provides you with all the security, access restrictions, etc offered by the Apache server and it's extensions.

This should get you started:

[http://www.debuntu.org/2006/05/20/54-how-to-subversion-svn-with-apache2-and-dav](http://www.debuntu.org/2006/05/20/54-how-to-subversion-svn-with-apache2-and-dav) (top of page to install, and "Confugring Apache" section to set-up)


There are other methods, 2 such examples are:

- By providing SSH access (which you have already said you dont want to do, but still worth considering as you can lock down the SSH capabilities for those accounts)

- Using a utility called svnserve, i've never used it before, and don't know how secure/effective it is, but it likely has less overhead than Apache if you've got a very slow subversion server machine.

Both of these are mentioned in this article: [http://www.geocities.com/asimshankar/notes/svn.html#remote_access](http://www.geocities.com/asimshankar/notes/svn.html#remote_access)


I can help you with the Apache method, but I've not had any experience with the others.

---

### Post by Naatan on 2007-05-23
I don't understand, I keep getting Permission Denied errors.. when I start the service as a demon and I do a co with svn://server.com it says authorisation failed without even asking for a login, when I do it with svn+ssh:// it asks for a login but then says permission denied.. and I'm definitely sure I'm using the right login...

My authz file looks like this:

```
[groups]
project_developer = dev,jan
[repository:/svn/project]
project_developer = rw
```

my passwd file is definitely correct, i'm sure of that.

Any idea what could be wrong?

---

### Post by SeanHodges on 2007-05-23
My guess is that you have decided to use svnserve with subversion for remote access.

You should see if svnserve is actually listening on a port. use "netstat | grep -i svn" to see if anything comes up. You could also try "svn co svn+ssh://localhost/home/svn/project1/" on the server itself to see if you can actually check something out at all.

I don't know a lot about svnserve tho, so hopefully pansz might be able to help you with any tricky stuff ;)

---

### Post by Naatan on 2007-05-23
Yea I used svnserve, but after that kept giving me problems I tried the apache method and that worked :)

Only the connection is really slow.. whilst the websites running on the same apache server dont have any problems.. weird, oh well I'm willing to live with that.

---

