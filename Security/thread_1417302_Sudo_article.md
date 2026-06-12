---
title: "Sudo article"
date: 2010-02-27
forum: Security
---

### Post by dogdo on 2010-02-27
see [http://www.longitudetech.com/blog/linux-unix/the-perils-of-sudo-with-user-passwords/](http://www.longitudetech.com/blog/linux-unix/the-perils-of-sudo-with-user-passwords/)

So sudo use is not that secure-should i run a ubuntu user account with no sudo access at all?

---

### Post by Bachstelze on 2010-02-27
The article's reasoning is flawed right from the start.

> a compromised user account [...] is instantly root in most setups.

By the same logic, I could say that on a "traditional setup", there is the risk of compromizing the root account, and that this makes the setup not secure.

Obviously, if you're running a default Ubuntu setup (admin user can run any commands with root privileges), you should give your admin account the same level of security you would give to the root account in a traditional setup. In both cases, you must give strong security to one account. The flaw of the Ubuntu model is when you give your admin user the same level of security you give to any other user. Don't do that, and you will be fine.

> Everything should be done from a root shell, and you should have to know an uber-secret root password to access anything as root.

That's great, because my user password, that I use to run sudo stuff with, *is* "uber-secret".

---

### Post by OpSecShellshock on 2010-02-27
The article's concerns apply more to enterprise environments than to home use. But even if we accept that the net effect of using a root shell and using sudo from a user account with admin privileges is the same, and one method tells you who the actual user was while the other method doesn't, sudo still works out to be the better practice on balance.

And the point the article seems to miss the most is that in an enterprise environment, *all* legitimate access needs to be audited, because legitimate access is a weak point. It has nothing to do with whether or not the admins can be trusted with root.

Also, while it's true that if a user's password is compromised and that user has sudo access you have a problem, it's also true that there are ways for local users without such access to get around it. A stolen password is a stolen password. But in a pass-the-hash scenario, putting in the extra step of requiring sudo+password on a user account is still another barrier that a direct root login doesn't have. There's more than one way to compromise a machine. And that's my biggest problem with the article: it seems to presume that you can just parse out security considerations and deal with them individually rather than as interrelated parts of a complex whole.

---

### Post by mkvnmtr on 2010-02-27
Was this question solved with the sudo update I got this morning on a couple of my machines?

---

### Post by Bachstelze on 2010-02-27
> **mkvnmtr said:**
> Was this question solved with the sudo update I got this morning on a couple of my machines?

What question?

---

### Post by OpSecShellshock on 2010-02-27
The sudo update isn't related to the linked article. The article is speaking more to the general ideas behind its use in contrast to a direct root login.

But it's still good to install the update, of course.

---

### Post by bodhi.zazen on 2010-02-27
IMO sudo is no more and no less secure then using su. 

The main point of sudo is it allows finer grain of control to root access.

root / su is all or none, sudo can be all or none, but it can also allow access to more limited range of commands.

If an account is compromised I would assume root access is not far behind. This applies equally to systems using sudo and su.

IMO it is senseless to argue over which is more secure and learn the advantages and disadvantages of the two.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by Bachstelze on 2010-02-27
> **bodhi.zazen said:**
> 
If an account is compromised I would assume root access is not far behind. This applies equally to systems using sudo and su.

It really depends on what kind of environment we're talking about. For entreprise or university systems with thousands of users, it seems inevitable to me that someone, some day, will make a mistake that will result in his account being compromised. Of course, you can't let that have an impact on the system as a whole.

That's basically what the author of the article is saying: some people in such environments are apparently using [font=monospace]sudo[/font] in a very wrong way (I don't know any, but I'm totally willing to believe such people exist).

@dogdo: Please read this article carefully. Does it say anything that applies to you? No. And even if it did, you wouldn't necessarily have to drop [font=monospace]sudo[/font] altogether, just learn how to use it better.

---

### Post by OpSecShellshock on 2010-02-28
> **Bachstelze said:**
> That's basically what the author of the article is saying: some people in such environments are apparently using [FONT=monospace]sudo[/FONT] in a very wrong way (I don't know any, but I'm totally willing to believe such people exist).

Well yes, that is a pretty wrong way to use sudo. Switching over to su or a direct root login wouldn't solve that problem though, and might inadvertently cause other problems. Especially in environments which require daily access audit reports.

---

