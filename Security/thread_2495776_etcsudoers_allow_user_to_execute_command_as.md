---
title: "/etc/sudoers allow user to execute command as"
date: 2024-03-01
forum: Security
---

### Post by Drenriza on 2024-03-01
Hi all

When using /etc/sudoers (visudo) how can i allow a non-sudo user to execute
1. 'drush' command
2. as 'apache' user
3. with all arguments available after 'drush' so for example
3.1 drush status
3.2 drush status --verbose
3.3 drush cr
3.4 drush -S --Something
3.5 etc.
without hard coding every possible drush command variation.

My current entry in /etc/sudoers is as follows

```

user1 ALL=(apache) NOPASSWD: /usr/bin/php /bin/drush
user1 ALL=(apache) NOPASSWD: /usr/bin/php /bin/drush status

```

If i run the command
```
$ sudo -u apache /usr/bin/php /bin/drush
# or
$ sudo -u apache /usr/bin/php /bin/drush status
```
it works as expected, but if i run

```
$ sudo -u apache /usr/bin/php /bin/drush status --verbose
```
the command no longer matches what is written in /etc/sudoers and fails

Using '*' after drush
```
user1 ALL=(apache) NOPASSWD: /usr/bin/php /bin/drush *
```
is not really an option, since this would possible allow permission escalation

I considered creating a user script to call from /etc/sudoers that could sanitize the drush inputs, but that is more complicated than as such.

Any input / advice would be greatly appreciated.

Thank you in advance
Best regards

---

### Post by TheFu on 2024-03-01
I think you want to check out the "Parameter_List"  or "Parameter" options in the sudoers.  It is possible to block specific options using **'!'*** or **-=** . I've never used these, so I don't have first hand knowledge.  From the manpage:

```
     Parameters may be flags, integer values, strings, or lists.  Flags are implicitly
     boolean and can be turned off via the ‘!’ operator.  Some integer, string and
     list parameters may also be used in a boolean context to disable them.  Values
     may be enclosed in double quotes ("") when they contain multiple words.  Special
     characters may be escaped with a backslash (‘\’).

     Lists have two additional assignment operators, += and -=.  These operators are
     used to add to and delete from a list respectively.  It is not an error to use
     the -= operator to remove an element that does not exist in a list.
```


Also, 
```
   Wildcards
     sudo allows shell-style wildcards (aka meta or glob characters) to be used in
     host names, path names and command line arguments in the sudoers file.  Wildcard
     matching is done via the glob(3) and fnmatch(3) functions as specified by IEEE
     Std 1003.1 (“POSIX.1”).

     *         Matches any set of zero or more characters (including white space).

     ?         Matches any single character (including white space).

     [...]     Matches any character in the specified range.

     [!...]    Matches any character not in the specified range.

     \x        For any character ‘x’, evaluates to ‘x’.  This is used to escape spe&#8208;
               cial characters such as: ‘*’, ‘?’, ‘[’, and ‘]’.

     Note that **_these are not regular expressions_**.  Unlike a regular expression there
     is no way to match one or more characters within a range.
....

```
It goes on with examples and exceptions and caveats.  Be very careful using the '*' wildcard, even at the end of a filename, since any other files can be added and will be provided access.  There's a warning about this.

I always setup aliases for long commands just for me.  For long commands that I want others to have, I create scripts and drop them into /usr/local/bin/ for everyone to have access.

I don't know if this is sufficient, but I hope it provides leads for testing. Just because something works, don't assume it won't allow things you don't want.

---

### Post by Drenriza on 2024-03-14
Thank you TheFu
For the great feedback!

---

### Post by TheFu on 2024-03-14
manpages already on our systems are amazing.

---

