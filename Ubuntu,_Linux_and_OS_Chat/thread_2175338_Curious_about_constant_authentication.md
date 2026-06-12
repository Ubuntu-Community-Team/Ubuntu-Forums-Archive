---
title: "Curious about constant authentication"
date: 2013-09-18
forum: Ubuntu, Linux and OS Chat
---

### Post by jgw on 2013-09-18
I am curious about authentications.  If I want to do anything, that might change something, I must enter my password for authentication.  If I want to change two things, one thing after another, then I must enter my password two times.  I also realize that I can deal with this problem by doing everything in a terminal and issuing a "sudo -i" (I think), however, that would obviate the use of any of the unity buttons, etc.  At the same time I am told that its a really bad idea to log in as root.  One would think, however, that if one does log in then that login might have a, say, 10 minute window.  Since my ignorance continues, insofar as Ubuntu is concerned, there may actually be a way to do this.  Anyway, and I may be completely alone in this one, is it at all possible to do something about this?  Are there existing fixes?  

Just wondering - thank you..........

---

### Post by deadflowr on 2013-09-18
Are you constantly opening and closing a terminal window or something?
Because, there is a default timeout of something like 15 minutes for authentication per session.
When I run sudo anything, I have roughly 15 minutes wherein I can sudo something else without a need for a password prompt.
This ends when I close a terminal session.

It can be extended, I forget the line but adding something like timestamp_timeout=<biggernumber> to the sudoers file will change the default timeout to whatever you set.
This might help
[http://ubuntuforums.org/showthread.php?t=763142](http://ubuntuforums.org/showthread.php?t=763142)

---

### Post by mJayk on 2013-09-18
From what he said I think he means GUI based modifications i.e. in the settings windows?

---

### Post by jgw on 2013-09-19
I am talking about editing a file, installing anything, etc.  My example of a terminal was to mention the "sudo -i" which will log you in, as root, and as long as the terminal is open you remain logged in.  What I am really talking about is some kiund of time limit on an authentication outside of a terminal.  

Just a thought - thanks for the replies.......

---

### Post by craig10x on 2013-09-19
It's just part of the many great security features that comes standard in linux distros...:D

---

### Post by deadflowr on 2013-09-19
If the app launches as root(super user) without a need to run sudo or gk/kde/su(do)
then chances are it uses pkexec.
That, I have no clue on how to extend it's time limit.
This might give you a clue or something.
[http://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo](http://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo)

But in general, most programs lose their elevated privileges when they close.
If they didn't, it would leave a gaping security hole.

---

### Post by buzzingrobot on 2013-09-22
Unix/Linux employ a system of permission intended to keep users from mucking about with files they don't own. Since the root user owns most of the files, and all of the important ones, we users can't mess with them unless we are allowed temporary root privileges.

Today, with one machine per person, we grant ourselves those temporary privileges.  If we break something, we're the only losers. But, the OS traces its lineage to a time when one machine supported any number of users logged in at the same time. 

Authentication requests can be annoying while you're setting up a machine.  Once that's done, you shouldn't see many at all during routine use.

---

### Post by mastablasta on 2013-09-23
i only see those when doing updates.

it's a security feature and it doesn't po up unless you are changing system files. if oyu are changing system files for example in text editor running as root then not closing the editor should keep the root privilege open.

---

### Post by 3rdalbum on 2013-09-24
Policykit has a need for authentication every time, but note that Policykit doesn't actually run the application as root. It only runs one function with extra privileges, which is how it should be.

Sudo and Gksudo have timeouts and work seperately to Policykit. They run a whole program as root.

If you put your password into a Policykit-enabled program, it doesn't extend the Gksudo timeout. Unfortunately.

But once you have your system set up, you should rarely encounter Policykit or Gksudo.

---

