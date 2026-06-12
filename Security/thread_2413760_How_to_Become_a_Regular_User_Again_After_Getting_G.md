---
title: "How to Become a Regular User Again After Getting Gaining Superuser Privileges"
date: 2019-03-01
forum: Security
---

### Post by John_Patrick_Mason on 2019-03-01
Hi again,

I have a bit of problem. Because my computer has a limited amount of RAM, I don't like too many users to be logged in at the same time on my Ubuntu system, so I will often log out other users with:

```
sudo killall -u username
```

since I don't have their password. The problem is after I type in the above command I'd like to use the computer right away without waiting for my administrative privileges to expire. Is there a quick command that I can type into the terminal that would revert my account back to a regular user account?

---

### Post by DuckHook on 2019-03-01
Ehrmm, excuse me if I'm misinterpreting something, but this is a pretty nuclear-option action that you are invoking. Do you at least give these other users a chance to save their work? If it were me, I'd be awfully angry at being blasted out of the system in the way you describe.

As for your question, again, I'm not sure if I am misunderstanding your issue: by using *sudo*, I assume you are already operating from within your regular user account. After you have nuked those other user sessions (and assuming that you haven't nuked your own) you simply carry on in your current session—which should already be a regular user account. The elevated privileges only come into play if you invoke *sudo* again (which expire within 5 or 10 minutes anyway—can't remember the exact time). Absent the use of *sudo*, you are already operating as a regular user in a regular account and should be able to continue doing so without interruption.

---

### Post by John_Patrick_Mason on 2019-03-01
[QUOTE=DuckHook]Ehrmm, excuse me if I'm misinterpreting something, but this is a pretty  nuclear-option action that you are invoking. Do you at least give these  other users a chance to save their work? If it were me, I'd be awfully  angry at being blasted out of the system in the way you describe.[/QUOTE]

Don't worry, I know what I'm doing. The reason I use:

```
sudo killall -u username
```

is because the person sometimes forgets to log out using the GUI, and I don't want to know their password. The person in question is, of course, my dad, so there's no worry of accidentally erasing unsaved work since he doesn't know how to use LibreOffice or anything, just the internet; he's not very tech-savvy, in other words.

The reason I was asking if there existed a command to revert my account back to a regular user account is because I believed that once I typed:

```
sudo killall -u username
```

that I would temporarily have superuser privileges, thereby temporarily making me vulnerable if I decide to surf the web, kind of like being logged in to your administrative account while surfing the web on Windows, unless if I'm mistaken. Aren't you vulnerable for 5-10 minutes if you decide to browse the internet right after you decide to use the sudo command? To be clear, it says that I'm an administrator under System Settings > User Accounts >  Account Type. I'm not sure now if that means I'm a standard user that's different from a regular user in that I'm allowed to use sudo, or if I AM an administrator at all times. I thought being an "administrator" on Ubuntu 16.04 meant that you were a standard/regular user that is able to use sudo.

---

### Post by DuckHook on 2019-03-01
Ah. Understood.

As for your question about sudo, it does not *elevate* your regular account into superuser privilege. That's not how sudo works. It only elevates the execution of the one instance of a command following the invocation of sudo. So long as you don't preface a command with sudo, you are executing such commands as a regular user. So, unless a nasty website tricks you into invoking sudo, you will be surfing as your regular user. I assume that you would refuse if some questionable website asks you to execute a command prefaced with sudo.

The fact that your regular account is set as an administrator account is not only normal, but necessary. All this means is that you have the right to invoke sudo. It does not mean that you operate as a superuser by default. Obviously, every system must have at least one account that has administrator rights. Otherwise, no one could invoke sudo, which would make maintenance, well… awkward, to say the least.

If you wish to practice extra security and forestall nasty websites (a laudable goal which too few pay attention to, in my opinion), you could do many things to harden your browser. Some of those strategies are explained in my sig under: Security Basics.

Here's a past posting of mine that is now pretty long in the tooth, but still has some validity: [https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795](https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795)

More recently, I have taken to completely sandboxing my browser by running it in a VM. Since VMs are so easy to set up these days, and since modern machines have more than enough resources, this is usually a good solution for many browser concerns.

Hope this helps.

---

### Post by 1clue on 2019-03-01
One further thing:

Let's you have 10 terminals open and a web browser with 10 tabs, and 3 other apps running.

You select terminal 1 and you type 'sudo patricide'. When you successfully type your password, you kill your father's account. For the next few minutes, if you type 'sudo' again in front of a command, you will execute that command as root, without requiring a password.

However, it's only that one terminal which has any sort of escalation. Terminals 2-10 will ask for a password if you type 'sudo' in front of something. Your web browser does not run escalated, and nor do any of the other apps.

When the timer expires on your first terminal, then you will need to type your password after 'sudo' again on that terminal too.

---

### Post by John_Patrick_Mason on 2019-03-01
Got it! That makes much more sense security-wise. Also on using sudo, back when I was an absolute beginner, it would infuriate me when I would see tutorials with the sudo command, without explaining what it meant. They would explain what the command following sudo meant, but not sudo itself. I was always afraid to type commands into the terminal that I did not understand, and even today I still refuse to do so, unless I understand every single command in a tutorial. I'm marking this thread as solved. Thanks for your time.

EDIT: Just read 1 clue's post. Ha! But if you're like me and like to do everything through the terminal, and you type:

```
sudo firefox
```

after typing your password. Wouldn't you then be vulnerable to attack when browsing the internet?

---

### Post by DuckHook on 2019-03-01
> **John_Patrick_Mason said:**
> …and you type:

```
sudo firefox
```

after typing your password. Wouldn't you then be vulnerable to attack when browsing the internet?

Yes, you would. It is absolutely foolish to run a browser as the superuser. It would also have a high probability of borking you user environment even without visiting a bad website: has to do with messing up permissions running a graphical app under sudo.

It is a good idea to invoke GUI apps through the GUI and CLI apps through the CLI. Keeps things straighter that way.

---

### Post by 1clue on 2019-03-01
I frequently run gui apps from the terminal since the terminal is by far my most-used app. I don't really see any harm in that.

The part about putting 'sudo' in front of a web browser command though, that's insanity and an invitation to sacrifice your computer to the dark gods of the net. No matter what the browser, and no matter what the site. Just don't do it, ever.

There used to be some sanity in using lynx to go to the distro's documentation page to read how-to's but these days black hats hack into those sites too, and you never know what a search engine will give you.

---

### Post by 1clue on 2019-03-01
So just to straighten this out in your mind: 


[LIST=1]
[*]Apps shouldn't run escalated unless there's a really good reason to do so.
[*]GUI apps which make sense to run escalated have a provision to run escalated built-in. For example, Synaptic Package Manager. It inherently requires privilege escalation because it installs and removes packages.
[*]When you login as a privileged user and run a normal app, the safeguards are gone.
[*]That's why Ubuntu has gone through the trouble to disable the root user by default. This is the main reason I use Ubuntu so much instead of Debian or some other distro. I agree 100% with their approach on this.
[/LIST]

There is no reason whatsoever to login as root, or to run any long-running process as root on any sort of regular basis.

---

### Post by &amp;KyT$0P# on 2019-03-02
> **1clue said:**
> When the timer expires on your first terminal, then you will need to type your password after 'sudo' again on that terminal too.

You can also manually expire the timer by running this in the same terminal -
```
sudo -K
```

Refer to [FONT=Courier New]man sudo[/FONT] for more info

---

