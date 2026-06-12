---
title: "Go back to trollschool with the Great GPL Autotroller!"
date: 2009-05-18
forum: The Cafe
---

### Post by monsterstack on 2009-05-18
I don't pretend to be good at Python: I'm pretty terrible, really. Still. Here's an automatic troll script for you all. Save the text as "whatever.py", and then run it with

```
python whatever.py -n    # for trolling Linux users and their OS.
python whatever.py --nix #
python whatever.py -w    # for trolling Windows users and their OS.
python whatever.py --win #
```

Everybody hates trolls. This is just a bit of fun to see if I could replicate the dumb things they say. So the next time you see a stupid troll post, just remember the guy who wrote it probably wouldn't pass the Turing Test. 

```

#! /usr/bin/env python
#
# The Great GPL Autotroller! Now with added incoherence!

import getopt, sys, random, sys, string

# Nasty words for Microsoft and Windows:
msnouns     =   [ "M$", "microsuck", "windoze", \
                  "winbloze", "winsuck", "win00bz", \
                  "winborg", "wincrud" ]

# Nasty words for Linux:
nixnouns    =   [   "lunix", "freetard lunix", "opensores", "poonix" ]

# Nasty words for users:
pronouns    =   [ "lusers", "fools", "idiots", \
                  "jerks", "fanbois", "poop-eaters", \
                  "morons", "prisoners", "lovers", "lamers" ]

# Nasty verbs for the failings of the OS.
obverbs     =   [ "sucks", "blows", "stinks", \
                  "fails", "runs like turd", \
                  "doesnt even work properly", "loses", \
                  "is not ready for the desktop" ]
                  
# Nasty verbs for the failings of users.                  
ppverbs =   [ "suck", "fail at life", "suck so hard", \
              "lose at everything", "cant even use a terminal", \
              "are stupid", "are lame", "smell bad" ]

# Additional adverbs. Because you really mean it.              
adverbs =   [ "...BADLY", "...BIG TIME", "so much", "seriously", \
                    "", "" ]



def main():
    """Using getopts and sys.argv, we get the terminal input and use it
       to work out what trollish output the user desires."""
#
# First, try to get an option from the user.
    try:
        opts, args = getopt.getopt(sys.argv[1:], "nwh", ["win","nix","help"])

# If that fails, print an error message and the usage instructions.
    except getopt.GetoptError, err:
        print str(err) 
        usage()
        sys.exit(2)

# Now parse the options and select the appropriate insult.
    for o, a in opts:
        if o in ("-n","--nix"):
            return random.choice([angrytroll("nix")[0],angrytroll("nix")[1]])
            sys.exit()
        elif o in ("-w","--win"):
            return random.choice([angrytroll("win")[0],angrytroll("win")[1]])
            sys.exit()
        elif o in ("-h", "--help"):
            usage()
            sys.exit()
        else:
            assert False, "unhandled option"


def usage():
    """Prints simple usage instructions."""
    print """Use -n for a Linux troll, and -w for a Windows troll.
    
                Example: python supertroll.py -n"""
    
############################
# TROLL LOGIC STARTS HERE! #
############################

def angrytroll(choice):
    """First insult: noun verb adverb. 
    Second insult: noun pronoun person-verb adverb."""
    if choice == "win":
        a = str(random.choice(msnouns))
    elif choice == "nix":
        a = str(random.choice(nixnouns))
    b = str(random.choice(obverbs))
    c = str(random.choice(adverbs))
    insult1 = " ".join([a,b,c])
    
    if choice == "win":
        a = str(random.choice(msnouns))
    elif choice == "nix":
        a = str(random.choice(nixnouns))
    b = str(random.choice(pronouns))
    c = str(random.choice(ppverbs))
    d = str(random.choice(adverbs))
    insult2 = " ".join([a,b,c,d])
    list = [ insult1, insult2 ]

    return list

if __name__ == "__main__":
    print main()


```

Please go right ahead and make it better if you like.

---

### Post by sim-value on 2009-05-18
Wait ... Python has no Semikolons ?! BLASPHEMY !!!!1

---

### Post by hansdown on 2009-05-18
A printable poster would be cool.

---

### Post by monsterstack on 2009-05-18
> **sim-value said:**
> Wait ... Python has no Semikolons ?! BLASPHEMY !!!!1

FINE.

```

breakit = open('/home/you/whatever.py','r')
for x in breakit.readlines():
    print "".join(str(x).replace(')',';').replace('(',';').replace('=',';'))
```

Semicolons everywhere!!!

---

### Post by calrogman on 2009-05-18
Epic win, not like a script run on Winbl0ws. /troll

---

