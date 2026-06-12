---
title: "Simple security question on folder access permissions"
date: 2007-01-17
forum: Server Platforms
---

### Post by stickmangumby on 2007-01-17
Hi everyone,
I'm in the process of figuring out how to help a friend set up a server. He has Ubuntu 6.06 Server installed on it already, and someone else has been helping him use it and I'm going to take over. I'm starting to get to know Linux, and I'm making progress pretty quick. I'm at a stage where I'm learning about stuff in the /etc directory and how to do most things with the command line. Anyway, that's just to give you an idea of my depth. Not a novice, but by no means an expert.

So, my (first) question is this:

If I'm setting up multiple local users, is it enough to chmod 700 their /home/username directory to protect it from other local users accessing it? Do I need to recursively set permissions on all their subfolders and files, or is this enough? If I do, can I change the default permissions to 700? That is, when a user creates a new file, can it automatically be set to drwx--------?

Thanks for the help, I have a feeling I'm going to be back with a lot more questions!

---

### Post by jtc on 2007-01-18
Actually, I'd rather set 711 on their homedirectories. There are times when a daeomon might want to enter an read a certain file. One example is the maild reading the users .fordward file.

When it comes to setting file permissions recusivly I wouldn't use the number-notation. If you give all the files 700, you'l be giving the x-flag to files which doesn't need it. Better then to relativly specifiy go-rwx (remove r, w and x from group and others). Just remeber that there a a few files, as mentioned above, which you might want to keep globally readable.

To make sure all new files are created with proper file-permissions you can add a umask to your /etc/bash.bashrc file. In your case the line would be umask 0077
(of course, this asuming you'r using bash.)

---

### Post by stickmangumby on 2007-01-18
Thanks for the reply jtc.

I'm not sure if I understand 711... from messing around with it for the past half hour, it seems execute means if you know the name of a file with read privileges for other (such as a directory) you can run/open it? Isn't this a possible problem if you can guess obvious file names or directories (ie docs)?

As far as I know the server is simply used as a file server for windows users, does this make 700 an ok option if there aren't any config files going to be accessed by programs they use?

Sorry to be a pain, I want to make sure it is secure before I do anything.

---

### Post by jtc on 2007-01-18
Well, the x-flag (value 1) has a double meaning. When it comes to files it, as you say, it is the right to run them, but when it comes to directories it is right to enter them. When I say you should have 711 on the homedir itself I'm only refering to the directory, not all files within them.

To access a file you both need the right to enter the directory where it is located AND the right to access it in the way you intend (read and/or run). Anyway, I'd say that the best way to get a feel for the diffrent accessrules is simply to play around with them.

Still, if it's only used as a fileserver 700 should work just as well.

But it is going to be used connected to by Windows computers you say? Then you'll be dealing with Samba? If that's the case the umask-setting I suggested won't matter. Instead you'll want these two lines in your smb.conf

```

create mask=0600
directory mask=0700

```

---

### Post by stickmangumby on 2007-01-18
> **stickmangumby said:**
> I want to make sure it is secure before I do anything.

[QUOTE=jtc]When I say you should have 711 on the homedir itself I'm only refering to the directory, not all files within them.[/QUOTE]

So 711 will be secure for the homedir if subdirs and files are given correct access permissions. For example, .blah config files are given rwxr--r-- so that programs and daemons can access them, but subfolders and user created files should be 700 so that nothing else can access them? Is this generally correct?

Samba is tomorrows homework :P

Thanks again!

---

### Post by jtc on 2007-01-18
> **stickmangumby said:**
> So 711 will be secure for the homedir if subdirs and files are given correct access permissions. For example, .blah config files are given rwxr--r-- so that programs and daemons can access them, but subfolders and user created files should be 700 so that nothing else can access them? Is this generally correct?
Yes, that's basicly correct, except that most config-files don't need to be globally readable either. When you start a program it's run with your userid and has your permissions.

---

