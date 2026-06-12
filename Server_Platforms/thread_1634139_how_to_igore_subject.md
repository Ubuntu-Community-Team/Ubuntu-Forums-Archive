---
title: "how to igore subject"
date: 2010-11-30
forum: Server Platforms
---

### Post by wasanzy on 2010-11-30
Hi,

I have this:

:0H
* ^To.*support@dot.com.gh
| /usr/bin/mail_filter

which runs a program. But I want to add some thing to it so that, if the  subject contain a particular string, the program shouldn't be run. How  do I do that?

Thanks

---

### Post by SeijiSensei on 2010-11-30
> **wasanzy said:**
> Hi,

I have this:

:0H
* ^To.*support@dot.com.gh
| /usr/bin/mail_filter

which runs a program. But I want to add some thing to it so that, if the  subject contain a particular string, the program shouldn't be run. How  do I do that?

Thanks

To use nested criteria in procmail, just put them together like this:

```

:0H
* ^TO.*support@dot.com.gh
{
    :0
    * ^Subject:.*Something to ignore
    $DEFAULT

    :0
    | /usr/bin/mail_filter
}

```

This delivers messages with the matching subject to the default location (usually /var/spool/mail/username) and sends the rest to the filter.

I recommend using the ^TO built-in variable in most cases since it matches things like Cc: as well.

If you want to require matches against multiple criteria, use

```
:0
* criterion 1
* criterion 2
disposal
```

as a recipe.  This will only employ "disposal" when both criteria are met.

---

