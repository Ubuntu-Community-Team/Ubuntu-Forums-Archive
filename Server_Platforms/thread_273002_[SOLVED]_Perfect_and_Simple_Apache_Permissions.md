---
title: "[SOLVED] Perfect and Simple Apache Permissions"
date: 2006-10-07
forum: Server Platforms
---

### Post by altonbr on 2006-10-07
I have notes on how to set up an Apache server from my Linux class last semester, but I'm having a couple problems (partially because we learned on Apache1 and now I'm using Apache2)

> _Root Directory:_
**/var/www**
_changed to:_
**/home/brett/www/altonbr.dyndns.org**

**/home/brett** should be **750 & brett.brett**
**/home/brett/www** should be **770 & brett.www-data**
**/home/brett/www/altonbr.dynds.org** should be **770 & brett.www-data**
**/home/brett/www/altonbr.dynds.org/index.html** should be **755 & brett.www-data**

Nonetheless, I don't know if Apache2 can even read /home/brett/www ... so where did I go wrong? the owner brett is so I can edit files, and the group www-data is what Apache gives users surfing on port 80 to my IP correct?

My error is:

> **[SIZE="6"]Forbidden[/SIZE]**

[SIZE="3"]You don't have permission to access / on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.[/SIZE]

What did I do wrong?

Lastly, I added brett to the www-data group.

---

### Post by sonic2000gr on 2006-10-07
Ok let's try to keep this as simple as possible...

By default UNIX and Linux assign to home folders 755 permissions. That means:

Owner: All permissions (rwx)
Group: Read / Execute (r_x)
Other (Everyone else): Read / Execute (r_x)

What you do have right now in /home/brett according to your post is:

750 with owner:group being brett:brett. Is that right?

With these permissions, apache can not get into the www, he does not even have permission to get into /home/brett. Apache is represented by the 0 in the above permissions, since owner and group are brett:brett.

There are many ways to get apache in there, but it all depends on what permissions you want to set to other (interactive) users.

Simplest would be:
```

sudo chmod -R 755 /home/brett 
```

In this way anyone can read your files (not change them!) and apache will also be able to read anything in /home/brett/www. You should however go into your /home/brett directory and remove any superflous permissions. For example, if you have a folder mysecrets you want to keep secret, then:

```

sudo chmod -R 700 /home/brett/mysecret 
```

(Usually you would want to do this in your .pgp folder and anything else with private keys in it)

Should you wish to have apache be able to write to a folder e.g. /home/brett/www/altonbr.dyndns.org/incoming you could do:

```

sudo chown -R brett:www-data /home/brett/www/altonbr.dyndns.org/incoming
sudo chmod -R 775 /home/brett/www/altonbr.dyndns.org/incoming

```

It is generally not a good idea to allow apache full permissions on every file of the site. It should be limited to a folder where it really needs to write data.

This is only one possible scenario. Another one would be:

- Allow apache into your home directory
- Forbid any other user

Then you could do:

```

sudo chown -R brett:www-data /home/brett
sudo chmod -R 750 /home/brett

```

Essentially allows you to do anything you want with your files and apache to read them. Everyone else is blocked. Once again you should protect individual folders inside your home by applying specific permissions, and allow apache to write to a folder if that is desirable.

There are more options to this, but I hope this stuff will get you started.

---

### Post by altonbr on 2006-10-08
Yes, it was my permisson of 750 for /home/brett that was causing Apache the problem. So I made /home/brett brett:brett and 755 and then made /home/brett/www brett:www-data 750 ... that setup seems to work perfectly... now what about files like index.html or maybe even the inc or includes folder? What are good permissions and owners for those? Is there a tutorial I should read?

Thanks for your help though... much appreciated!

---

