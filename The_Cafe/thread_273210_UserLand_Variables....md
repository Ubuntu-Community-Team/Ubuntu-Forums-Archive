---
title: "UserLand Variables..."
date: 2006-10-07
forum: The Cafe
---

### Post by Mr. Picklesworth on 2006-10-07
I thought of this a while ago, when I realized how limited a conventional windowed GUI is compared to a CLI.
With a CLI, I can get a program to run after another program. This means that I could have a file upload then shut down, or attach a timer to the poweroff command so that it doesn't happen for 12 hours.

When I'm running a windowed GUI, I am not given this power; to do the above, I still have to go to the terminal and enter the necessary commands.


So, thus sparked a thought which I am sure many have had, but I may as well write. (*I thought* I invented double buffering :b)
It really is quite simple, but the effects could be tremendous. 
It's effectively environment variables, but in a more fleshed out way. I believe that such a thing could give Linux that obvious feature which puts it a step above the competition.

The thought is to have an API which allows software developers to 'tag' variables (or functions?) as "user-space variables" (or something like that).
A simple function could be used which assigns a string to a particular variable pointer, along with (optionally) a quick description / other data.

Then, another application could use the user-space variable API and determine all sorts of handy information such as what user-space variables have been created, what application they were created by, etcetera.
This program could be used to schedule tasks.

For example:
I'm downloading a video via BitTorrent, but I also want it converted to a particular format by the time I get home. Normally this is a troublesome task unless the BitTorrent program has a video converter built in or it has a nice "after download run this" option.
-So, I open the task scheduler and it reports a few user variables created by my BitTorrent software.
-There appears to be one for "File x Progress", so I choose to create an event when it is equal to "Finished" (chosen from a dropdown menu of options; this hypothetical variable has some extra data attached to it specifying that it has a few set values which it can be equal to - a task scheduler like this one wouldn't be an integral part of the API but rather a seperate program of which there could be many variations).
-This event could close the program and shut down the computer, because I know that torrent program is a bit clumsy and can forget its progress with other files if it's forced to shut down. There would definitely be at least one option: Close program. But perhaps there could also be a few user functions attached to this program. (For sanity's sake, those functions could be called by the program itself when a particular variable is set to 1; the task scheduler is really just seeing that variable and reading a bit of attached information saying it is to call a function. For now, I'm not going to think about security). Hm... there appears to be a "Close without sanity check" function here, so I'll use that. It's added to the event queue.
-Next, I could tell the scheduler to run the shutdown function to turn off the computer.
-Joy!

Now comes the further dreaming:
The possibilities don't have to end there, and don't have to all come at once.

Perhaps the GUI could set values for the user-space variables system, or (since the last thought could be horrendously resource-wasting) a particularly nice task scheduler could look through the GUI for buttons and labels.
Then, if an application doesn't set user variables itself, it can still be scheduled in fancy ways. For instance, if a progress bar becomes full or if a label changes to Finished a program is closed. Or, maybe, if a video converter is launched, a button (recognized by values that aren't expected to change, like name and position; the Handle of the button would change if this is a new instance of the program that the scheduler is thinking of) is pressed.
That would be a bit of a power-user thing, but still nice.

Maybe (even more dreamily) that dream task scheduler could observe the user's action, and notice that the user keeps pressing the "Cancel" button which keeps appearing in a window called "Error" (which won't go away!), and suggest to help with that by clicking it for him. Or maybe it could observe that the user is always setting the "Mode" setting in a program to "Modelling" within 5 seconds of starting it, so it suggests to do that for them. (Since the program won't bother to remember, the scheduler will).

From the surface this seems a simple idea, but in retrospect it still would need a lot of work.
The API would need to work and it would need to be foolproof, a solid task scheduler - including some form of GUI recognition and hopefully with the ability to recognize variables/gadgets by things other than their current handle - would need to be built to really drive home the possibilities, and someone smart would have to fill in the various potential security holes.

So, essentially, this is work that I honestly must admit I can't do myself. (Well, I could write a task scheduler but I wouldn't put myself anywhere near an API).

What do you think of this idea?
Does it sound like it would be nice, unsafe, useless, or like something that you read every week?
Any thoughts on what could and could not be done, and what kind of work is really involved?

Thanks very much in advance!

---

### Post by Bloodfen Razormaw on 2006-10-07
Sounds like you want things to work like KDE, with task-based operations that let you perform a single task in what appears an atomic way even if it really requires several steps, and with scriptable applications as with DCOP; just taken to a more complete level, in which much more of the operation is task based and much more of the program is made scriptable.

---

### Post by Tomosaur on 2006-10-07
Just use the terminal :/

---

### Post by maniacmusician on 2006-10-07
it sounds like a pretty cool way to create a workflow, if i'm understanding it correctly. didnt mac have something like that? not as efficient, but it would allow you to create a workflow in a similar way, but with not as much control as this.

---

