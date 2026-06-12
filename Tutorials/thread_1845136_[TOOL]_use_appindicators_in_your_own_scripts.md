---
title: "[TOOL] use appindicators in your own scripts"
date: 2011-09-16
forum: Tutorials
---

### Post by reda_ea on 2011-09-16
With tools like zenity or yad simple useful scripts can be made completely graphical.
However, none of these support the new appindicators in ubuntu (I think yad does the -now hidden- tray icons)
So I made a little script that does this, probably still needs some improvement but it gets the job done.

OK so here's how to use it. 
The command takes the menu elements from standard input, each line containing the path of the element in the form
```
menu:submenu:..:entry
```
The appindicator will then be shown with then menu, and once the user makes a choice it will be closed and that choice (the full path as given in the input line) will be echoed to standard output.
small example:
```

(cat <<EOF
hello:world
hello:
hello:big
hello:small

goodbye
EOF
) | ./cappind.py

```
btw an empty entry name means separator

Ok so what about a real indicator, one that stays displayed and does actual stuff.
There's the --persist option that keeps the indicator displayed (and adds a quit option at the bottom). Example:
```

(cat <<EOF
_Aa
b:1
b:2
c
EOF
) | ./cappind.py --persist | while read s; do
case "$s" in
	_Aa ) echo hello ;;
	b:1 ) echo big ;;
	b:2 ) echo small ;;
	c ) echo world ;;
esac
done

```

and even that is not needed as the same code could be written without --persist
```

CONT=true
while $CONT; do
case "`(cat <<EOF
_Aa
b:1
b:2
b:
b:q
c
EOF
) | ./cappind.py`" in
	_Aa ) echo hello ;;
	b:1 ) echo big ;;
	b:2 ) echo small ;;
	b:q ) export CONT=false ;;
	c ) echo world ;;
esac
done

```
you get the idea...

there's also the -i/--icon option to give an icon name - this must be the name of an icon from the theme (application names and generic names).
either way all options are displayed on the help screen
```
cappind.py --help
```

That's it. What next ?
* a way to add icons to the menu ?
* a way to support ":" in the labels ? (is this even necessary)
* a way to specify, on the input, the commands to be executed ?
* input from a file (-i/--input) ? a command ?
* a timeout (so the menu can be refreshed periodically) ?
* other ideas ? 
I'd like more suggestions, but the main things are:
* I only want this to do appindicator support (one tool for one job)
* A change in input format should not break compatibility with the old format
* A simple task should require a simple format (EX: a simple list of choices is a list of lines not containing ":")

---

### Post by suzumeuta on 2011-10-13
This is just great. 

Although I still cannot find a good use for indicators (I might need more examples, but no one seems to know this app!), it's great to have support ready for them. For the record, this works neatly in KDE4, which is just really good.

Add one vote for icon support, though.

---

