---
title: "Execute command doesn't work on &quot;sudo&quot;"
date: 2012-03-05
forum: Server Platforms
---

### Post by satimis on 2012-03-05
Hi all,

I was following

Postfix Virtual MailBox Clam Smtp Howto
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto?action=recall&rev=82](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto?action=recall&rev=82)

building an mail server, creating /usr/local/sbin/deldovcotuser to delete users.

However it can only work as root.  On running;

$ sudo deldovecotuser [email]user@mydomain.com[/email]```

read: 18: Illegal option -n

Aborting....

```

it complains.

$ cat /usr/local/sbin/deldovecotuser ```

 #!/bin/bash
#
# deldovecotuser - for deleting virtual dovecot users
#
if [ ! $# = 1 ]
 then
  echo -e "Usage: $0 username@domain"
  exit 1
 else
  user=`echo "$1" | cut -f1 -d "@"`
  domain=`echo "$1" | cut -s -f2 -d "@"`
  if [ -x $domain ]
   then
    echo -e "No domain given\nUsage: $0 username@domain: "
    exit 2
  fi
fi
read -n 1 -p "Delete user $user@$domain from dovecot? [Y/N]? "
echo
case $REPLY in
 y | Y)
  new_users=`grep -v $user@$domain /etc/dovecot/users`
  new_passwd=`grep -v $user@$domain /etc/dovecot/passwd`
  new_vmaps=`grep -v $user@$domain /etc/postfix/vmaps`
  echo "Deleting $user@$domain from /etc/dovecot/users"
  echo "$new_users" > /etc/dovecot/users
  echo "Deleting $user@$domain from /etc/dovecot/passwd"
  echo "$new_passwd" > /etc/dovecot/passwd
  echo "Deleting $user@$domain from /etc/postfix/vmaps"
  echo "$new_vmaps" > /etc/postfix/vmaps
  postmap /etc/postfix/vmaps
  postfix reload
  read -n1 -p "Delete all files in /home/vmail/$domain/$user? [Y/N]? " DELETE
  echo
  case $DELETE in
   y | Y)
    echo "Deleting files in /home/vmail/$domain/$user"
    rm -fr /home/vmail/$domain/$user
   ;;
   * )
    echo "Not deleting files in /home/vmail/$domain/$user"
   ;;
  esac
 ;;
 * )
  echo "Aborting..."
 ;;
esac

```

adddovecotuser works on sudo.  


$ ls -ld /usr/local/sbin/deldovecotuser```
 
-rwxr-xr-x 1 root staff 1256 Mar  5 17:13 /usr/local/sbin/deldovecotuser

```

$ ls -ld /usr/local/sbin/adddovecotuser ```

-rwxr-xr-x 1 root staff 1678 Mar  5 16:52 /usr/local/sbin/adddovecotuser

```

Google didn't find me a solution.  Please help.  TIA

B.R.
satimis

---

### Post by hawkmage on 2012-03-05
Doing a cut and paste of your code and removing the commands to do the actual removal of accounts and files I am not having an issues running your script using sudo.

If you run the command:
```
cat -vet /usr/local/sbin/deldovecotuser
```
Are there escaped chars on the first read command on line 18?

---

### Post by satimis on 2012-03-05
> **hawkmage said:**
> Doing a cut and paste of your code and removing the commands to do the actual removal of accounts and files I am not having an issues running your script using sudo.

If you run the command:
```
cat -vet /usr/local/sbin/deldovecotuser
```
Are there escaped chars on the first read command on line 18?

Just performed;
$ cat -vet /usr/local/sbin/deldovecotuser > deldovecotuser.txt

on deldovecotuser.txt;
line 18```

read -n 1 -p "Delete user $user@$domain from dovecot? [Y/N]? "$

```

B.R.
satimis

---

### Post by satimis on 2012-03-06
Hi all,

Problem solved as follow:-

on /user/local/sbin/deldovecotuser

line 18:-```

read -n 1 -p "Delete user $user@$domain from dovecot? [Y/N]? "

```

it left out ":" (semcolon) after "?"

After adding it "sudo deladvecotuser" works without problem.  But I don't understand why root works even without ":" after "?"

satimis

---

