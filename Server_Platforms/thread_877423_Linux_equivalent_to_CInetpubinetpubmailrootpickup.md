---
title: "Linux equivalent to C:\Inetpub\inetpub\mailroot\pickup\"
date: 2008-08-01
forum: Server Platforms
---

### Post by brianmolidor on 2008-08-01
Is there a linux equivalent to C:\Inetpub\inetpub\mailroot\pickup\ ?
 (you can drop an email into this directory and it will be picked up and sent out)

What I'm trying to do is send an email from a MySql Trigger,
This works great in windows:
```

select "To: email@email.com","From: email@asdf.com","Subject: blah","","blah" 
into outfile "/inetpub/mailroot/pickup/mail.txt"
fields terminated by '\r\n';

```

In Ubuntu Linux I have tried the following:
```

select "To: email@email.com","From: email@asdf.com","Subject: blah","","blah" 
into outfile "/var/mail/mail.txt"
fields terminated by '\r\n';

```
AND
```

select "To: email@email.com","From: email@asdf.com","Subject: blah","","blah" 
into outfile "/var/spool/mail/mail.txt"
fields terminated by '\r\n';

```
With no luck.

Anybody know if there is a mail folder like this on Linux? Or will I have to find another route of sending email through MySql triggers?

Any help would be appreciated. Thank you

---

### Post by cariboo on 2008-08-01
Might be a dumb question, but do you have a MTA (mail transfer agent) setup? Exim4 is installed by default in the sever installation, but you might want to have a look at Postfix.

Jim

---

### Post by windependence on 2008-08-01
/var/mail/spool is the closest thing I can think of, but I don't think you can just send from it.

Are you using php top run the front end of this database? If so, you could use the mail() function to send.

I'm not really quite sure what you mean by sending mail through MySQL triggers, but then I'm not a DBA either. :)

-Tim

---

### Post by StickyStyle on 2008-08-02
I do not know of type of directory you can just drop mail into with postfix (the closest thing i can think of is /var/spool/postfix/incomming - but that's just for the pickup agent), and there is no xp_sendmail() type of func in MySQL.  
I see two solutions, one is to have a script that runs out of cron every minute or so doing a select on the table where you want the trigger looking for new rows (assuming your trigger was ON INSERT) and then have the script send the email.  The other is to continue with your trigger that writes a file into a directory (that you create) and you have a second script that is watching for new files and submits them to the email server.

---

### Post by brianmolidor on 2008-08-03
After a bit of searching, i found a similar, easy to use, MySQL Mail Query. (It's a Module or Plug-in)

I did not make this, but A HUGE thanks to [http://jan.kneschke.de/projects/mysql/udf]("http://jan.kneschke.de/projects/mysql/udf") for posting such valuable code. Thank you.

```

#include <mysql.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

my_bool mail_init(UDF_INIT *initid, UDF_ARGS *args, char *message) {
        initid->maybe_null = 0;

        return 0;
}

long long mail(UDF_INIT *initid, UDF_ARGS *args, char *is_null, char *error) {
        char *prg;
        FILE *p;
        int i;

        if (args->arg_count != 2) {
                strcpy(error, "MAIL() needs receipient and body");
                return 1;
        }

        if (args->arg_type[0] != STRING_RESULT ||
            args->arg_type[1] != STRING_RESULT) {
                strcpy(error, "MAIL() needs receipient and body as string");
                return 1;
        }

        for (i = 0; i < args->lengths[0]; i++) {
                char c = args->args[0][i];

                if (!((c >= 'a' && c <= 'z') ||
                      (c >= 'A' && c <= 'Z') ||
                      (c == '@') ||
                      (c == '.') ||
                      (c >= '0' && c <= '9') ||
                      (c == '-' ) ||
                      (c == '_' ))) {
                        strcpy(error, "the receipient contains a illegal char");

                        return -1;
                }
        }

        prg = malloc(strlen("/usr/lib/sendmail ") + args->lengths[0] + 1);
        strcpy(prg, "/usr/lib/sendmail ");
        strcat(prg, args->args[0]);


        p = popen(prg, "w");

        free(prg);

        if (NULL == p) {
                strcpy(error, "opening pipe failed");
                return -1;
        }


        fwrite(args->args[1], args->lengths[1], 1, p);
        fclose(p);


        *is_null = 0;
        *error = 0;

        return 0;
}

```

**-- how to compile --**
gcc -I /usr/local/mysql/include/ -shared -o udf_mail.so mail.c -Wall

Now copy file into /usr/lib
cp udf_mail.so /usr/lib/

I had to edit mysql.h file to compile this successfully. I just remarked out an include statment for mysql_version.h.in

**-- how to install into MySQL --**
Execute the following query:
```
create function mail returns integer soname 'udf_mail.so';
```

**-- how to send mail in MySQL --**
This can be executed as a query! *gasps of "WOW" and "COOL"*
```
select mail('email@domain.com', 'Subject: UDF Mail\r\n\r\nYou got mail');
```


This works great in triggers and as a stand alone executed sql statement.

Thanks for your help everybody!

---

### Post by mahe23 on 2010-06-24
Hi Brian,

I am new in Ubuntu.

I try to compile but without success.

**-- how to compile --**
gcc -I /usr/local/mysql/include/ -shared -o udf_mail.so mail.c -Wall

1. I do not have the directory:/usr/local/mysql/include/
2. The code you show. Is this the file mail.c? and the compiled file udf_mail.so?

Matthias

---

