---
title: "Restrict users to subversion only"
date: 2007-10-02
forum: Server Platforms
---

### Post by [h2o] on 2007-10-02
I setup a subversion repository for a school project using svn+ssh. The repository is located in /home/projectuser/svnroot but we wanted to see who commited what, so I created additional users on my machines for them and added them to the group "projectgroup" and changed the group owner of the repository to this group and chmoded g+rxw.
Now, this seem to work.

But, I don't want these users to have access to the rest of the machine. I want them to be able to use the svn-repository, and nothing else.
I tried setting the shell to /dev/null but then they could not authenticate and thus not use the repository.

Any advice?

---

### Post by jodeet on 2007-10-02
Maybe pam will help here.  In pam, there is the concept of 'session' controls.  I think you might be able to configure a pam session directive that specifies the login shell that a member of a specific group will get.

So, for example, you might make a group that all svn users belong to.  Then, in /etc/pam.d/ssh, you might add a session type directive that says the login shell should be /usr/bin/svn or something like that.

I think you might need to add whatever shell you specify to /etc/shells, in order to be able to ssh in.

Alternatively, you could make an entry in /etc/passwd for each user that will use svn, and make the login shell be /usr/bin/svn.  Again, you'd have to add /usr/bin/svn to /etc/shells.

---

### Post by HermanAB on 2007-10-02
Actually, the 'Ubuntu Way' is to do this kind of thing with sudo, as defined in the /etc/sudoers file.

What you need to do is create a group for this and make the users members of that group, then put an entry in sudo that allows only that group to run the svn binaries.  This way you have extremely fine grained control.

Read the sudoers man page for details.  

If the users run a graphical tool, then you have to invoke gtksudo to ask for the password and launch the program.

Cheers,

Herman

---

### Post by Loevborg on 2007-10-10
One solution is to set up a public key infrastructure and use command="/usr/bin/svnserve ..." .ssh/authorized_keys

See:
[http://svn.collab.net/repos/svn/trunk/notes/ssh-tricks](http://svn.collab.net/repos/svn/trunk/notes/ssh-tricks)

---

### Post by hyper_ch on 2007-10-10
Maybe this could help:

[http://felipecruz.com/blog_restricte-linux-users-to-their-home.php](http://felipecruz.com/blog_restricte-linux-users-to-their-home.php)

Well, not the RPM in there but the way you could accomplish that.

---

