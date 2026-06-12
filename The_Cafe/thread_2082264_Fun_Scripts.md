---
title: "Fun Scripts"
date: 2012-11-08
forum: The Cafe
---

### Post by hookitup on 2012-11-08
hello folks, 

so i wana see what fun scripts ppl come up with. lets have fun and post some fun useful shell scripts. post it in code wrapping and give it a name that describes what it does and possible a small description.

KEEP IN MIND this is not to discuss issues or problems with a script, lets keep it clean and have fun.

this is my fake logon script. 

so basically what this script does when ran at login via terminal, is it will first say "access denied" as if you got the password wrong then ask you to retype it, but security its a fake logon , so you would enter the [COLOR="blue"]name that you specified[/COLOR] and if correct it will let you in but if wrong i will kill that session with the username [COLOR="lime"]specified at the bottom of the sript[/COLOR]

I edited my /etc/bash.bashrc file to run at login (vis SSH)
I edited my /etc/pam.d/login and /etc/pam.d/sshd to get rid of the junk that shows up at login
I ran touch ~/.hushlogin to get rid of the other junk at login

here is the script
```
#!/bin/bash

S="sleep .5"
N="~"
Name="[COLOR="Blue"]some name[/COLOR]"

echo "Access denied"
$S
read -s -p "`whoami`@[COLOR="red"]ipaddress[/COLOR]'s password:" username
echo ""

if [ "$username" = "$Name" ];then
        echo 'Success!!! You are now logged in.'
else
        echo 'Sorry, Access Denied.'
        echo $N
        $S
        echo $N
        $S
        echo $N
        $S
        echo "*~~~ip logged~~~> `who`"
        echo 'Good Bye'
        pkill -KILL -u [COLOR="Lime"]username[/COLOR]
        pkill -KILL -u [COLOR="lime"]another username[/COLOR]
fi

```

text in colors you will have to change for your system
if you mess this script up some how and it just automatically logs you out you can always CTRL+C to cancel it before it kicks you out. (i learned this the hardway :))
any questions about my script just fell free to PM me.

---

### Post by drmrgd on 2012-11-09
Here's a fun python one that you can use as part of other python scripts.  I don't remember where I found it (I need to take better notes!):

```
#!/usr/bin/python

import sys
import time

dt = 0.06

string=raw_input("Enter any string you like: ")

#string = """Lorem ipsum dolor sit amet, consectetur adipiscing elit.
#Etiam est mauris, egestas sit amet fermentum et, viverra vitae odio. 
#In nec molestie mi."""

for phrase in string.split('.'):
        p = phrase.strip()
        if not p:
                continue
        for s in p:
                sys.stdout.write(s)
                sys.stdout.flush()
                time.sleep(dt)
        sys.stdout.write('\n')
        sys.stdout.flush()
        time.sleep(dt*10)
```

You can run it with 'python script_effect.py' and then once it's running enter in a string of text and hit return.  If you want to increase or decrease the speed, just change the value of 'dt'.  You can also comment out the input statement and uncomment the string variable if you want to have it spit out pre-defined text.

I also thought this one was rather neat to play with.  This comes from a Lars Nooden on this forum in answer to someone who wanted to put together a perl script to take text and print it upside down:

```
#!/usr/bin/perl
# From Lars Nooden at ubuntu forums.  Takes input string and prints the string upside down.

use strict;
use warnings;
use utf8;

binmode(STDOUT, ":utf8");

my %flipTable = (
    "a" => "\x{0250}",
    "b" => "q",
    "c" => "\x{0254}", 
    "d" => "p",
    "e" => "\x{01DD}",
    "f" => "\x{025F}", 
    "g" => "\x{0183}",
    "h" => "\x{0265}",
    "i" => "\x{0131}", 
    "j" => "\x{027E}",
    "k" => "\x{029E}",
    "l" => "l",
    "m" => "\x{026F}",
    "n" => "u",
    "o" => "o",
    "p" => "d",
    "q" => "b",
    "r" => "\x{0279}",
    "s" => "s",
    "t" => "\x{0287}",
    "v" => "\x{028C}",
        "u" => "n",
    "w" => "\x{028D}",
        "x" => "x",
    "y" => "\x{028E}",
        "z" => "z",
    "." => "\x{02D9}",
    "[" => "]",
    "(" => ")",
    "{" => "}",
    "?" => "\x{00BF}", 
    "!" => "\x{00A1}",
    "\"" => ",",
    "<" => ">",
    "_" => "\x{203E}",
    ";" => "\x{061B}",
    "\x{203F}" => "\x{2040}",
    "\x{2045}" => "\x{2046}",
    "\x{2234}" => "\x{2235}",
    "\r" => "\n",
    " " => " "
);

while ( <> ) {
    my $string = reverse( $_ );
    while ($string =~ /(.)/g) {
        print $flipTable{$1};
    }
    print qq(\n);
}
```

Just run the script, type in some text, and have fun :D  Hit Ctrl+D when you're done seeing funny text output.  Occasionally you might get an error that says "Use of uninitialized value..." which means you've typed a character that's not in the list.  You can just look it up and add it from either of these sources:

[http://en.wikipedia.org/wiki/List_of_Unicode_characters](http://en.wikipedia.org/wiki/List_of_Unicode_characters)
[http://www.upsidedowntext.com/unicode](http://www.upsidedowntext.com/unicode)

---

### Post by Statia on 2012-11-09
> **drmrgd said:**
> Just run the script, type in some text, and have fun :D  Hit Ctrl+D when you're done seeing funny text output.  Occasionally you might get an error that says "Use of uninitialized value..." which means you've typed a character that's not in the list.  You can just look it up and add it from either of these sources:

[http://en.wikipedia.org/wiki/List_of_Unicode_characters](http://en.wikipedia.org/wiki/List_of_Unicode_characters)
[http://www.upsidedowntext.com/unicode](http://www.upsidedowntext.com/unicode)

That would be nice to run on a proxy that is serving flipped images for the Upside-down-ternet :-)

[http://www.ex-parrot.com/pete/upside-down-ternet.html](http://www.ex-parrot.com/pete/upside-down-ternet.html)

---

