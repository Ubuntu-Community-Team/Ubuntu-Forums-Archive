---
title: "svn commit causes gnome pwd request but pwd not accepted"
date: 2010-08-26
forum: Security
---

### Post by cppljevans on 2010-08-26
I recently upgraded from ubuntu 8.04 to 10.04 using a live cd.
I had been posting updates to [http://svn.boost.org/svn/boost/sandbox/variadic_templates/](http://svn.boost.org/svn/boost/sandbox/variadic_templates/)
for several years now.

However, now I'm getting:
```

~/prog_dev/boost-svn/ro/sandbox/rw/variadic_templates/libs/composite_storage/sandbox/pack  $ svn commit one_of_multiple_dispatch.test.cpp 

** (emacs:10831): CRITICAL **: murrine_style_draw_box: assertion `height  >= -1' failed 

** (emacs:10831): CRITICAL **: murrine_style_draw_box: assertion `height  >= -1' failed 

** (emacs:10831): CRITICAL **: murrine_style_draw_box: assertion `height  >= -1' failed 
Password for '(null)' GNOME keyring: 
svn: Commit failed (details follow): 
svn: MKACTIVITY of  '*/svn/boost/*!svn/act/9179ad19-b1e9-434c-a9ec-a14e5c9e33dd':  authorization failed: Could not authenticate to server: rejected Basic  challenge ([https://svn.boost.org]("https://svn.boost.org/")) 
svn: Your commit message was left in a temporary file: 
svn:  '/home/evansl/prog_dev/boost-svn/ro/sandbox/rw/variadic_templates/libs/composite_storage/sandbox/pack/svn-commit.2.tmp' 
~/prog_dev/boost-svn/ro/sandbox/rw/variadic_templates/libs/composite_storage/sandbox/pack  $ 

```What may be relevant is I installed gpg; however, I'm a newbie at gpg and security in
general.

What should I do to enable my using svn commit again?

TIA.

---

### Post by cppljevans on 2010-08-30
The following post described a solution for me:

[http://subversion.tigris.org/ds/viewMessage.do?dsForumId=1065&dsMessageId=2402527](http://subversion.tigris.org/ds/viewMessage.do?dsForumId=1065&dsMessageId=2402527)

---

