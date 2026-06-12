---
title: "Simple Recomendation"
date: 2007-12-16
forum: Ubuntu Brainstorm
---

### Post by superatrain on 2007-12-16
In resent Ubuntu releases, if a user tries to run a program from terminal that is not installed, they will get a helpful hint of how to install the program with apt. I feel that this should be expanded to cover more areas of trouble for users. If a user uses apt or other common root-only applications as their own user, they will get unexpected, and sometimes, scary looking results.

```
$ apt-get install program
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

That should be something more helpful and user friendly, such as:
```
$ apt-get install program
Notice: You have tried to run an administrator-access level application.
This application could harm your computer, so you need to verify that you are actually an administrative user of this computer.
Enter the command "sudo apt-get install program" to continue.

```

Or, for less harmful operations, it can even redirect directly to sudo, and have them type their password without retyping the command.


Also, users should be warned when running commands such as "rm -rf", "rm -r *" and other such dangerous commands that have unfortunately been given to unsuspecting users.

---

### Post by smartboyathome on 2007-12-16
The second part of your suggestion has already been done in another thread.

The first part I would say it should be something like this:
```
$ apt-get install program
Notice: This program needs to be run as root.
To run it as root, type sudo apt-get install program
```

---

### Post by bikeboy on 2007-12-17
> **smartboyathome said:**
> 

The first part I would say it should be something like this:
```
$ apt-get install program
Notice: This program needs to be run as root.
To run it as root, type sudo apt-get install program
```

Yeah that puts it nice and concisely, but still makes it more user friendly. Would be a good improvement.

---

### Post by Hobbsee on 2007-12-17
sounds like a good wishlist bug for apt/dpkg/aptitude/etc.  Maybe even Command-Not-Found, if it were to be further generalized.

---

### Post by coolen on 2007-12-20
I'd like to see applications that require root priveledges routed to sudo. I fail to see how it's any sort of security risk, since it still requires a password (although there are likely esoteric backdoors which could be exploited).

I think new users might be frustrated by having to constantly prove, not that they are an administrator, but that they are able to type the word "sudo" before a command.

---

### Post by st4rdr1ft3r on 2007-12-20
add them to the bash aliases?

---

### Post by coolen on 2007-12-20
Possible, but you can download additional programs which require root priveleges. They'd have to add their own alias, and that doesn't cover new users.

Is there an exit status set for hey-you're-not-root? If so, could bash be made to catch that, check if you're part of the admin group, and re-route to sudo? Although I don't know how you'd get it to suppress output beforehand, so this would spit out an error then run...

---

### Post by smartboyathome on 2007-12-20
> **coolen said:**
> Possible, but you can download additional programs which require root priveleges. They'd have to add their own alias, and that doesn't cover new users.

Is there an exit status set for hey-you're-not-root? If so, could bash be made to catch that, check if you're part of the admin group, and re-route to sudo? Although I don't know how you'd get it to suppress output beforehand, so this would spit out an error then run...

I think policykit may handle what you are wanting to do (though I have not used it, but it is going into GNOME).

---

