---
title: "Mailman Installation, please help."
date: 2007-07-24
forum: Server Platforms
---

### Post by jimslim on 2007-07-24
using this FAQ: [https://help.ubuntu.com/7.04/server/C/mailman.html](https://help.ubuntu.com/7.04/server/C/mailman.html)

I got up to the part where it tells me to make a mail list, but I can't get any further! This is what terminal tells me:


```
jim@server:/$ sudo /usr/sbin/newlist mailman
Enter the email of the person running the list: jim@jim.com
Initial mailman password: 
Create a new, unpopulated mailing list.

Usage: /usr/sbin/newlist [options] [listname [listadmin-addr [admin-password]]]

Options:

    -l language
    --language=language
        Make the list's preferred language `language', which must be a two
        letter language code.

    -u urlhost
    --urlhost=urlhost
        Gives the list's web interface host name.

    -e emailhost
    --emailhost=emailhost
        Gives the list's email domain name.

    -q/--quiet
        Normally the administrator is notified by email (after a prompt) that
        their list has been created.  This option suppresses the prompt and
        notification.

    -h/--help
        Print this help text and exit.

You can specify as many of the arguments as you want on the command line:
you will be prompted for the missing ones.

Every Mailman list has two parameters which define the default host name for
outgoing email, and the default URL for all web interfaces.  When you
configured Mailman, certain defaults were calculated, but if you are running
multiple virtual Mailman sites, then the defaults may not be appropriate for
the list you are creating.

You also specify the domain to create your new list in by typing the command
like so:

    newlist --urlhost=www.mydom.ain mylist

where `www.mydom.ain' should be the base hostname for the URL to this virtual
hosts's lists.  E.g. with this setting people will view the general list
overviews at http://www.mydom.ain/mailman/listinfo.  Also, www.mydom.ain
should be a key in the VIRTUAL_HOSTS mapping in mm_cfg.py/Defaults.py if
the email hostname to be automatically determined.

If you want the email hostname to be different from the one looked up by the
VIRTUAL_HOSTS or if urlhost is not registered in VIRTUAL_HOSTS, you can specify
`emailhost' like so:

    newlist --urlhost=www.mydom.ain --emailhost=mydom.ain mylist

where `mydom.ain' is the mail domain name. If you don't specify emailhost but
urlhost is not in the virtual host list, then mm_cfg.DEFAULT_EMAIL_HOST will
be used for the email interface.

For backward compatibility, you can also specify the domain to create your
new list in by spelling the listname like so:

    mylist@www.mydom.ain

where www.mydom.ain is used for `urlhost' but it will also be used for
`emailhost' if it is not found in the virtual host table. Note that
'--urlhost' and '--emailhost' have precedence to this notation.

If you spell the list name as just `mylist', then the email hostname will be
taken from DEFAULT_EMAIL_HOST and the url will be taken from DEFAULT_URL (as
defined in your Defaults.py file or overridden by settings in mm_cfg.py).

Note that listnames are forced to lowercase.

The list admin address need to be a fully-qualified address, like
owner@example.com, not just owner.

Illegal list name: mailman@server
```


The FAQ says it should work after this, but when i try to run mailman, i get this
```

jim@server:/$ sudo /etc/init.d/mailman start
 * Site list for mailman (usually named mailman) missing.
 * Please create it; until then, mailman will refuse to start.

```


Help please?

---

### Post by Mr. C. on 2007-07-25
The newlist script is failing:

```
Illegal list name: mailman@server
```

Provide a legal list name.

MrC

---

### Post by glenstewart on 2008-05-25
Edit /etc/mailman/mm_cfg.py and define DEFAULT_EMAIL_HOST and DEFAULT_URL_HOST there too.  The error and configuration instructions shown at install fail to mention that.

---

