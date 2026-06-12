---
title: "Catching whiptail checklist results in bash script"
date: 2012-12-29
forum: Ubuntu Application Development
---

### Post by sixfootseven on 2012-12-29
I have googled the heck out of this, and read dozens of examples, but cant quite figure it out...

I understand how the yes/no buttons work, and can catch those no problem, but I want to give several options to the user, and catch the output in my script, and do something with it.

```
#! /bin/bash

whiptail --title "Test" --checklist "Choose:" 20 78 15 \
"John" "" on \
"Glen" "" off \
"Adam" "" off \


# If "John" is selected, run this function:
function john {
echo "You chose John"
}

# If "Glen" is selected, run this function:
function glen {
echo "You chose Glen"
}

# If "Adam" is selected, run this function:
function adam {
echo "You chose Glen"
}

exit
```

I can see the output at the command line when the above script ends, but how can I use it inside the script?

Also, using the option "--seperate-output" seems to totally suppress the output, rather than seperate it on different lines like it is meant to.

I would appreciate any help :-)

---

### Post by Toz on 2012-12-29
Checklist sends its output to stderr, so you need to catch it somehow. Not sure if this is the best way, but here is one method:
```

#!/bin/bash

whiptail --title "Test" --checklist --separate-output "Choose:" 20 78 15 \
"John" "" on \
"Glen" "" off \
"Adam" "" off 2>results

while read choice
do
	case $choice in
		John) echo "You chose John"
		;;
		Glen) echo "You chose Glen"
		;;
		Adam) echo "You chose Adam"
		;;
		*)
		;;
	esac
done < results
```

---

### Post by sixfootseven on 2012-12-30
Thanks so much for your help. When I get a chance to test I'll come back and mark as solved.

Cheers.

---

### Post by sixfootseven on 2012-12-30
Thanks.

Your code worked great, and I really appreciate your help. 

Whiptail menus are the final touch on a multiinstaller program similar to Tasksel, but greatly expanded, that I am writing primarily for Raspbian, but will work on any Debian based system, so will test it on Ubuntu too, and make it available.

I tweaked a little to suit my needs, and heres the working sample code:

```
#!/bin/bash

function firstroutine {
 echo "running johns function"
}

function secondroutine {
 echo "running glens function"
}


function thirdroutine {
 echo "running adams function"
}

whiptail --title "Test" --checklist --separate-output "Choose:" 20 78 15 \
"John" "" on \
"Glen" "" off \
"Adam" "" off 2>results

while read choice
do
        case $choice in
                John) firstroutine
                ;;
                Glen) secondroutine
                ;;
                Adam) thirdroutine
                ;;
                *)
                ;;
        esac
done < results

```

---

### Post by sixfootseven on 2012-12-30
The Thread Tools menu does not contain a 'Solved' function for me to set.

Can someone educate me, or if I simply don't have access because I'm a n00bie, can someone please set as solved.

Thanks for all the fish.

---

### Post by BlinkinCat on 2012-12-30
> **sixfootseven said:**
> The Thread Tools menu does not contain a 'Solved' function for me to set.

Can someone educate me, or if I simply don't have access because I'm a n00bie, can someone please set as solved.

Thanks for all the fish.

Hi,

You as the OP have the ability of marking as solved.
Simply use the Thread Tools Menu at top of page and select "Mark as Solved"

Cheers - :)

---

### Post by sixfootseven on 2012-12-30
> **BlinkinCat said:**
> Hi,

You as the OP have the ability of marking as solved.
Simply use the Thread Tools Menu at top of page and select "Mark as Solved"

Cheers - :)
No I don't.

In Thread Tools, I have two options:

[LIST=1]
[*]Show printable options.
[*]Subscribe to this thread.
[/LIST]

And nothing referring to marking a thread as solved.

Cheers.

:)

---

### Post by BlinkinCat on 2012-12-30
> **sixfootseven said:**
> No I don't.

In Thread Tools, I have two options:

[LIST=1]
[*]Show printable options.
[*]Subscribe to this thread.
[/LIST]

And nothing referring to marking a thread as solved.

Cheers.

:)

Hi,

They are more like the options when you are not logged on. Are you sure you are logged on when you are viewing the post ? - other than that I have no explanation.

Cheers - :p

---

### Post by BlinkinCat on 2012-12-30
Hi again,

It may be that this is a specialized forum. I have had a quick look at previous threads and none appear to marked as solved. Marking as solved may be for all of the rest of forums other than a few specialized ones.

If you really wanted to, you could ask a question in the forum help section but actually it may not be worth worrying about. 

All the best - :p

Edit : you could also read the Sticky at top of page.

---

### Post by Elfy on 2012-12-30
Thanks for bringing this to our attention - something is afoot, I can't mark this solved either.

---

### Post by Elfy on 2012-12-30
@sixfootseven - try now please :)

---

### Post by cariboo on 2012-12-30
It worked for me, so whatever Elfy did, it worked. I changed it back to unsolved, so the op could do it.

---

### Post by Elfy on 2012-12-30
> **cariboo907 said:**
> It worked for me, so whatever Elfy did, it worked. I changed it back to unsolved, so the op could do it.

That'll be why it wouldn't let me unsolve it just now then :p

Just want the OP to check so we can be sure it's not just staff.

---

### Post by sisco311 on 2012-12-30
> **sixfootseven said:**
> 
I tweaked a little to suit my needs, and heres the working sample code:


This method creates a temp file (results). Don't forget to delete it. 

The basic method of dealing with temp files is something like:

```

...
tempfile=$(mktemp)
trap 'rm -f "$tempfile"' EXIT

whiptail ... 2> "$tempfile"

while read -r line
do
    ...
done < "$tempfile"
...

```

But, in this case there is no need for a temp file. You can pipe directly the stderr of whiptail to the while loop.

```

whiptail ... 2>&1 | while read -r choice ...
```

---

### Post by sixfootseven on 2012-12-30
Thanks everyone, I appreciate the continued help with whiptail. My little script is getting rather huge. Can't wait to show it off.

I guess I should learn python and implement the results in there instead at some point! 

I am now able to mark this thread as solved, and have done so.

---

### Post by Elfy on 2012-12-31
Excellent - that worked then :)

---

