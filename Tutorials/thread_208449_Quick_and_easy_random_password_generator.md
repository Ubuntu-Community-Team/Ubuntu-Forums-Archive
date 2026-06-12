---
title: "Quick and easy random password generator"
date: 2006-07-03
forum: Tutorials
---

### Post by ardchoille on 2006-07-03
I wrote this script in response to a user needing to generate quick random passwords.

```

#!/bin/bash
# This script creates a random password using sha1sum

echo "Enter the master password"
read -s MASTPASS

echo "Enter the reason"
read -s REASON

echo "Enter desired number of characters"
read -s DESNUM

echo
echo "Your random password is:"
echo $MASTPASS $REASON | sha1sum | cut -c1-$DESNUM
echo

```

As long as the MASTPASS stays the same, you can have hundreds of REASON replacements (eg. website, newuser, email, tarballpassword, etc) and only have to memorise the master password.

I hope someone finds it helpful :)

---

### Post by ardchoille on 2006-07-04
Did a bit of improving on the original:

```

#!/bin/bash
# This script creates a random password using sha1sum

MASTONE=x
MASTTWO=y
 
while [ $MASTONE != $MASTTWO ] ; do
        echo "Enter the master password"
        read -s MASTONE
        echo "Retype the master password"
        read -s MASTTWO
        if [ $MASTONE != $MASTTWO ] ; then
             echo "Password entries don't match, try again" 1>&2
        fi
done
 
echo "Enter the reason"
read -s REASON
echo "Enter desired number of characters"
read -s DESNUM
echo
echo "Your random password is:"
echo $MASTONE $REASON | sha1sum | cut -c1-$DESNUM
echo


```

---

### Post by maagimies on 2006-07-06
Thanx, this is great :)

---

### Post by gorilla_king on 2006-07-06
so i'm really new to this kind of stuff. mainly all i do is browse the web. 
so how do i run this. and if i make a file for it, what should the extension be? thank you.

---

### Post by henrikem on 2006-07-06
[QUOTE=gorilla_king]so i'm really new to this kind of stuff. mainly all i do is browse the web. 
so how do i run this. and if i make a file for it, what should the extension be? thank you.[/QUOTE]

Since it is a bash script, i would use .sh.

---

### Post by gorilla_king on 2006-07-06
> **henrikem said:**
> Since it is a bash script, i would use .sh.
lol, thanks you

---

### Post by Roderik on 2006-07-07
[EDIT] ow only read half the post, sorry :) this just makes random passwords :)

pwgen takes care of all your password generating needs :)

```
roderik@alucius ~ $ sudo apt-get install pwgen
roderik@alucius ~ $ **pwgen**
Lepi1een hahF2ahv IuYohch4 avi8AiB7 Jeo4ogho Deidee9a chah5Jah pee1Aiji
yohG4ai4 Shee4aic Owaa1bup Seixe3Ju Hi2okoph Cunee4Ee ooquuv7M ahH4yahn
aZ4oophi aevooS8Y za9ahNga Ki8ieduo Hei7eip4 eehee3Ie pe6Ugh5I eeThieD9
ook2Eeyu ahmaiD7G ii5ouHae Aethai7v Quei7uta shohS0oh Eghei3ui Uochee8a
Peeshei3 Tiezee6Y cuki0taR gubeeF6a ToeF0ey7 joo2Iedi Aevee0pe aigh4Iel
airoh0Bu AechieV6 xoo7aXai Yai9ohre yaed4ooS Som3Goh4 aexai5Ch meiree8E
bee3eWie iesheiN1 xei4An8e dahb7Shu ohD8Aiy4 aiNu4aec elueC7oh aet2Sha0
thei9Xir ooja4Yea lei3goCh Eiquah2a Fia8fius aiG5yee2 AhphieR4 ItheeL5i
Caegahp9 wahCh4Vu vohxa8Ch aiButh6M ieX8eeBa eeYoo5sh jahGe0Qu suug0Cha
ucuaCha6 Quu8iepa Mobae9qu sis0ahPh oe6Eepee na9Eithu shoogh0A chie6Nan
chee8EeM ooxoo1Sa uNiuthe6 Ier6eeDe ahy7Oqu7 Quu3jaed Ies7Hei4 shae8auS
oothuCi2 Shoh8eiK Oosh7Quo chei8Xoo photh4Ae iex8ea3I Oogie5ie ohP6yieh
oofo2aNg Sish1aiW och1Obie beuNg7To cee4iPah Pie3ahma jeThoos9 noh8Ohx4
Wohduip8 thu9ohLo Iwai5pou rei9ooGh Aiyeigh2 ahsh6aiB ovooj4Ix eaj5Eizu
Yae8cho9 meijie1Z aiK4bool OoDiwo5m Aivoan0c Wui0ahp7 Ogu3Muiy Ucah7Auz
Bii0Aich USh1dige UKo9Thab ohZ9Ahsu puY8youT roh5Ai4o Lair6rei dieB7AhK
aeShei5u uCh9erei aiHait1g sienie1X geefai2I ahrae7Ah ohb2Fahj Pa3aeph0
ucee5AeW maiX0di8 aeLoh1oj ahvohX6w Iek5ieno Oj0ahZee UGheeph0 Ciec5aev
Diesha4o kaeGah9U AePhai3u fohZae9c oiK0aec1 Cei9xied Thah0hoh laaMah2S
hom8Aepi aish6Euv Eenie0ae AeS4ooso AeFooX3I Ef6JohSh IeG4lool Aeng9cah
```

---

### Post by gorilla_king on 2006-07-07
i posted this on my site without even thinking. and i forgot to ask your permission. well, i'm using your script as a reference for others on how to make little scripts like that run. mainly because i was confused, so i thought others might be too. so i was wondering if i can have permission to use this small script on my very unpopular (and until, never mentioned to anyone) site. If you'd like to preview what it will look like and actually exaclty how it will be displayed. Go here [http://whatigoogle.com/index.php?gt=pages&id=17](http://whatigoogle.com/index.php?gt=pages&id=17)

---

### Post by NoobieDoobieDo on 2007-03-04
In the last line : 

```
echo $MASTONE $REASON | sha1sum | cut -c1-$DESNUM
```

you could add
```
static=`date +%s`
echo  $static $MASTONE $REASON | sha1sum | cut -c1-$DESNUM
```

This helps make it a bit more random IMHO.

---

### Post by madneon on 2009-02-07
> **NoobieDoobieDo said:**
> This helps make it a bit more random IMHO.

That breaks the idea of having the same password every time you enter same MASTPASS and REASON. [-X

---

### Post by michael_elite on 2010-07-17
There is no need to make a script for password generation. I you this command every time i need some random string.

[http://www.usermadetutorials.com/2010/06/quick-password-generator-in-bash/](http://www.usermadetutorials.com/2010/06/quick-password-generator-in-bash/)

I've used that command a lot of times - i change a lot of password every day - i work on a company with a lot of email accounts.

---

### Post by ded38fr on 2010-10-07
Hi,

You can also use:
  [http://www.desmoulins.fr/index_us.php?pg=scripts!online!genpass](http://www.desmoulins.fr/index_us.php?pg=scripts!online!genpass)

which is a "Human readable" online password generator.


Hoping this will help.

---

### Post by onemyndseye on 2010-10-07
Thanks for sharing - I love this little script!

Though I feel from some of the some of the replies that others do not completely see its use...


This script not only generates a random password for you but also gives you the ability to quickly recall that password using the master pass:

```

~: ./passgen.sh
Enter the master password
ubunturox

Enter the reason
github.com

Enter desired number of characters
10

Your random password is:
af95accd4c


```

Entering the same details every time will always result in your created password being returned.  very neat :)

---

### Post by ziekfiguur on 2010-10-07
I noticed that this script only generates passwords with lower case letters and digits.:(
So i made a different one that generates passwords that also contain  upper case letters (and its fairly easy to expand it to also give other  characters)
I'm not very good at bash so it's in python:
```

#!/usr/bin/env python

import sys, string, hashlib, getpass

ask_silent = getpass.getpass

def ask_normal(str):
    sys.stderr.write(str)
    return sys.stdin.readline()

if '-s' in sys.argv or '--silent' in sys.argv:
    ask_normal = getpass.getpass
else:
    sys.stderr.write('Warning, by default the reason and password length are not'
    ' read as passwords (your console will show what you type). If you do not '
    ' want this, use the -s or --silent option.\n')


mastone = 'x'
masttwo = 'y'
while mastone != masttwo:
    mastone = ask_silent("Enter the master password: ")
    masttwo = ask_silent("Retype the master password: ")
    if mastone != masttwo:
        sys.stderr.write("Password entries don't match, try again\n")

reason = ask_normal("Enter the reason: ")

passlength = 'ten'
while type(passlength) != type(10):
    try:
        passlength = int(ask_normal("Enter desired number of characters: "))
    except ValueError:
        sys.stderr.write("Please enter a number.\n")

characters = string.ascii_letters + string.digits # add other characters that can be used in your passwords here

hash = hashlib.sha256()
len_to_go = passlength
pwd = ''
while len_to_go:
    hash.update(mastone)
    hash.update(reason)
    binary_pass = [ord(c) for c in hash.digest()]
    pwd_part = ''.join([characters[i % len(characters)] for i in binary_pass])[0:len_to_go]
    len_to_go -= len(pwd_part)
    pwd += pwd_part

sys.stderr.write('Your password is:\n')
sys.stdout.write(pwd + '\n')


```This script can also generate passwords longer than 40 characters.
Please note that this script is not compatible with previous scripts in this thread.

btw. This script uses sha256 instead of sha1, but thats easily changed too if you want.

---

### Post by onemyndseye on 2010-10-09
very nice!!!

I really need to learn some Python.....  Im really too bash addicted!! LOL!

---

### Post by ziekfiguur on 2010-10-09
I noticed a bug in my previous script, the getpass function removes the newline but sys.stdin.getline() doesn't so the passwords generated with the -s option would be different from the passwords without that option.

Here is a fixed version: 
```

#!/usr/bin/env python

import sys, string, hashlib, getpass

ask_silent = getpass.getpass

def ask_normal(str):
    sys.stderr.write(str)
    return sys.stdin.readline()[0:-1] # remove the newline

def ask_master():
    mastone = 'x'
    masttwo = 'y'
    while mastone != masttwo:
        mastone = ask_silent("Enter the master password: ")
        masttwo = ask_silent("Retype the master password: ")
        if mastone != masttwo:
            sys.stderr.write("Password entries don't match, try again\n")
    return mastone

def ask_length():
    passlength = 'ten'
    while type(passlength) != type(10):
        try:
            passlength = int(ask_normal("Enter desired number of characters: "))
        except ValueError:
            sys.stderr.write("Please enter a number.\n")
    return passlength


def generate(master, reason, length):
    characters = string.ascii_letters + string.digits # add other characters that can be used in your passwords here
    hash = hashlib.sha256()
    len_to_go = length
    pwd = ''
    while len_to_go:
        hash.update(master)
        hash.update(reason)
        binary_pass = [ord(c) for c in hash.digest()]
        pwd_part = ''.join([characters[i % len(characters)] for i in binary_pass])[0:len_to_go]
        len_to_go -= len(pwd_part)
        pwd += pwd_part
    return pwd

def main_console(argv):
    if '-s' in argv or '--silent' in argv:
        global ask_normal
        ask_normal = getpass.getpass
    else:
        sys.stderr.write('Warning, by default the reason and password length are not'
        ' read as passwords (your console will show what you type). If you do not '
        ' want this, use the -s or --silent option.\n')

    if '-u' in argv or '--unsafe' in argv:
        master = ask_silent("Enter the master password: ")
    else:
        master = ask_master()

    reason = ask_normal("Enter the reason: ")
    length = ask_length()
    sys.stderr.write('Your password is:\n')
    sys.stdout.write(generate(master, reason, length) + '\n')

class PWGen_Window:
    def __init__(self, gtk, silent, unsafe):
        self.gtk = gtk
        self.silent = silent
        self.unsafe = unsafe
        self.window = self.gtk.Window(self.gtk.WINDOW_TOPLEVEL)
        self.window.set_title("PWGen")
        self.window.connect("destroy", lambda w: self.gtk.main_quit())
        self.vbox = self.gtk.VBox()

        self.add_mastone()
        self.add_masttwo()
        self.add_reason()
        self.add_size()
        self.add_buttons()

        self.pwlabel = self.gtk.Label()
        self.pwlabel.set_size_request(200, 20)
        self.vbox.pack_start(self.pwlabel, True, True, 5)

        self.window.add(self.vbox)
        self.window.show_all()
        self.clip = self.gtk.Clipboard()

    def add_mastone(self):
        box = self.gtk.HBox()
        label = self.gtk.Label("The master password:")
        label.set_size_request(165, 20)
        label.set_alignment(0, 0.5)
        box.pack_start(label, False, True, 5)
        self.mastone = self.gtk.Entry()
        self.mastone.set_visibility(False)
        box.pack_start(self.mastone, True, True, 5)
        self.vbox.pack_start(box, False, False, 2)

    def add_masttwo(self):
        if self.unsafe:
            self.masttwo = None
        else:
            box = self.gtk.HBox()
            label = self.gtk.Label("Retype master password:")
            label.set_size_request(165, 20)
            label.set_alignment(0, 0.5)
            box.pack_start(label, False, True, 5)
            self.masttwo = self.gtk.Entry()
            self.masttwo.set_visibility(False)
            box.pack_start(self.masttwo, True, True, 5)
            self.vbox.pack_start(box, False, False, 2)

    def add_reason(self):
        box = self.gtk.HBox()
        label = self.gtk.Label("the reason:")
        label.set_size_request(165, 20)
        label.set_alignment(0, 0.5)
        box.pack_start(label, False, True, 5)
        self.reason = self.gtk.Entry()
        if self.silent:
            self.reason.set_visibility(False)
        box.pack_start(self.reason, True, True, 5)
        self.vbox.pack_start(box, False, False, 2)

    def add_size(self):
        box = self.gtk.HBox()
        label = self.gtk.Label("the password size:")
        label.set_size_request(165, 20)
        label.set_alignment(0, 0.5)
        box.pack_start(label, False, True, 5)
        self.size = self.gtk.Entry()
        self.size.set_text('10')
        if self.silent:
            self.size.set_visibility(False)
        box.pack_start(self.size, True, True, 5)
        self.vbox.pack_start(box, False, False, 2)

    def add_buttons(self):
        box = self.gtk.HBox()
        self.show_button = self.gtk.Button("Show password")
        self.show_button.connect("clicked", self.show_pwcallback)
        box.pack_start(self.show_button, True, True, 5)
        self.clip_button = self.gtk.Button("Copy password to clipboard")
        self.clip_button.connect("clicked", self.clip_pwcallback)
        box.pack_start(self.clip_button, True, True, 5)
        self.vbox.pack_start(box, False, False, 2)

    def show_pwcallback(self, data):
        if self.pwlabel.get_text():
            self.pwlabel.set_text('')
            self.show_button.set_label("Show password")
        else:
            pwd = self.generate()
            if not pwd:
                return
            self.pwlabel.set_text(pwd)
            self.show_button.set_label("Clear password")

    def clip_pwcallback(self, data):
        pwd = self.generate()
        if not pwd:
            return
        self.clip.set_text(pwd)

    def generate(self):
        mastone = self.mastone.get_text()
        if self.masttwo:
            masttwo = self.masttwo.get_text()
        reason = self.reason.get_text()
        if self.masttwo and mastone != masttwo:
            dialog = self.gtk.MessageDialog(parent = self.window,
                                     flags = self.gtk.DIALOG_MODAL | self.gtk.DIALOG_DESTROY_WITH_PARENT,
                                     type = self.gtk.MESSAGE_WARNING,
                                     buttons = self.gtk.BUTTONS_OK,
                                     message_format = "\nThe master password is incorrect.")
            dialog.run()
            dialog.destroy()
            return
        try:
            size = int(self.size.get_text())
        except ValueError:
            dialog = self.gtk.MessageDialog(parent = self.window,
                                     flags = self.gtk.DIALOG_MODAL | self.gtk.DIALOG_DESTROY_WITH_PARENT,
                                     type = self.gtk.MESSAGE_WARNING,
                                     buttons = self.gtk.BUTTONS_OK,
                                     message_format = "\nNeed a number for size.")
            dialog.run()
            dialog.destroy()
            return
        return generate(mastone, reason, size)

def main_gtk(argv):
    import pygtk
    pygtk.require('2.0')
    import gtk
    silent = False
    if '-s' in argv or '--silent' in argv:
        silent = True
    unsafe = False
    if '-u' in argv or '--unsafe' in argv:
        unsafe = True
    window = PWGen_Window(gtk, silent, unsafe)
    gtk.main()

def usage(argv):
    sys.stderr.write('usage: {0:s} [options]\n'.format(argv[0])
                     + 'possible options are:\n'
                     + '    -c, --console   Don\'t open the GUI.\n'
                     + '    -s, --silent    Don\'t show the reason and password size.\n'
                     + '    -u, --unsafe    Don\'t ask to confirm the master password.\n\n')

def main(argv):
    if '-h' in argv or '--help' in argv:
        usage(argv)
        return

    if '-c' in argv or  '--console' in argv:
        main_console(argv)
    else:
        main_gtk(argv)

if __name__ == '__main__':
    main(sys.argv)

```This version also includes an other option: -u or --unsafe will not make the program ask for the master password twice. I also added a GUI that can copy the password to your clipboard without showing it :P
To run the console version use the -c or --console option.
If you use the console version I made sure all output but the password it to stderr, so you can easily pipe the password to another program or redirect it to a file.

---

### Post by jacobw0 on 2010-12-28
Zeikfiguur,

That script is awesome!

It should be in the default installation as far as I'm concerned.

:D

---

### Post by ziekfiguur on 2010-12-28
> **jacobw0 said:**
> Zeikfiguur,

That script is awesome!

It should be in the default installation as far as I'm concerned.

:D

Thank you. I actually found a bug (kind of) in it a while ago. It caused some characters to have a higher probability than other characters to get in the password. 
It's not very serious, but I thought I should fix it.

So, here is a fixed version, but please note that it is NOT compatible with the previously posted version (it will generate different passwords).

---

### Post by lungten on 2010-12-28
Those are some nice scripts. I think it will come handy some time.

For now, I use a tool called 'apg' which is available in Ubuntu repos. I've found it quite good so far.

---

### Post by geelsu on 2011-03-16
We have just been told about massive changes and conditions on password use to be implemented by July 31.   This looks like an excellent script to expand on and make work.  BUT .... I don't know a lick about python.

The requirements for Passwords:


[LIST]
[*]Must be 14 characters long.
[*]Must be a mix of UPPER, lower, numbers, and special characters.
[*]There can never be a sequence of 3 from any of those 4 groupings.  For example I can have ABC, but not ABCD or  @#$, but not @#$%.
[*]It can't have any part of your name in it.  I suppose this could be pulled from some $USER environment variable or from a getent passwd.
[/LIST]

I know this is a lot to ask, but if any brave soul should happen to take a stab at this, they would be the hero of many a Sys Admin working within the confines of Federal red tape.

---

### Post by SeijiSensei on 2011-03-16
sudo apt-get install makepasswd 

This script enables you to have a lot of control over the nature of the passwords it generates.  Type "makepasswd --help" for details.  You can force a minimum and maximum length and give it a string of valid characters.  Unfortunately it doesn't support regular expressions, so to use all the upper and lower alphanumerics and the specials, you need to use the --string option like this:

```
makepasswd --count=10 --chars=14 --string='abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789,.!@#$%^&*()\][{};":?-_+='
```

That will produce ten, fourteen-character passwords.  You might want to limit the number of specials in the list.  A sample run of the command above results in 

```

5@K6FX$wmOWMJV
$PilI.CM(Ky8F%
u&9F(AHCLTm[9@
S}ZI7j1L-LvHRM
n,s]PT]EWNr:,H
C7_(E-^Fqje.hN
@Xkh_kDqx&4*o?
{dd;",CN?Do9fQ
f(BwFT4Bni!hi\
Wz^TBPFND.i-E7

```

A more manageable password generator might be the Perl script mkpasswd.pl that you can install with "sudo apt-get install libstring-mkpasswd-perl".  That lets you control the number of each type of character in the passwords it generates.  For instance,

```
mkpasswd.pl -l 14 -s 2
```

generates a fourteen-character password with two special characters.

---

### Post by lyonya20011 on 2011-06-28
If you don't want or can't install anything, you can just use bash script I wrote for generating passwords, among other things, it can generate **truly** random passwords. You can find it here:[ https://github.com/lyonya20011/passwords]("https://github.com/lyonya20011/passwords")

---

### Post by ziekfiguur on 2011-06-28
> **lyonya20011 said:**
> If you don't want or can't install anything, you can just use bash script I wrote for generating passwords, among other things, it can generate **truly** random passwords. You can find it here:[ https://github.com/lyonya20011/passwords]("https://github.com/lyonya20011/passwords")

The point of the first solution was that it generates a strong password, that is not distinguisable from a truly random password. But, by using the script, still easy to remember (or generate).

---

### Post by JeshurunDaniel on 2011-11-25
Figaro's Password Manager does wonders for me.

```
sudo apt-get install fpm2
```

:popcorn:

---

### Post by leberblock on 2013-05-30
```
sudo aptitude install keepassx
``` ... saves my day! ;)

---

