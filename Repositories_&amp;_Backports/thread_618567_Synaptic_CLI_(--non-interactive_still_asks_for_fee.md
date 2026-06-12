---
title: "Synaptic CLI (--non-interactive still asks for feedback)"
date: 2007-11-20
forum: Repositories &amp; Backports
---

### Post by Tundro Walker on 2007-11-20
Here's the basic idea...

Musther did the AutoFSCK script, which delays FSCK until shutdown instead of bootup.  This is fantastic for folks who like to boot/shutdown their comps.  So, we had the idea to do the same with system updates...delay them until shutdown, so the user's bandwidth isn't eaten up d/l'ing them, and the CPU isn't bogged down loading them in when the user is trying to do something else (*cough* like playing an FPS *cough*)

(Before I continue further, yes, I know you can keep Linux comps on forever and don't have to shut them down.  But some of us like to shutdown our comps.  So, please don't troll this thread with non-productive comments like "just keep your computer on all the time.")

So, originally, Musther and I thought it'd be easy enough to just chain some apt-get commands together and call it from PostSession or such.  While this would be very easy, that command is poo-poo'ed upon a bit, because updating through Synaptic / Update Manager helps take care of more things than apt-get covers (not quite sure what, but it's just what I keep hearing ... "use Update Manager, not apt-get").

So, I figured we could use the "update-manager" or "synaptic" command via CLI or script, since they have command-line switches, and running either will still take the User's Update preferences into account (EG: like just doing security fixes, keeping or deleting install packages when done, etc).

Problem with update-manager is that it always asks for User confirmation before doing anything.  We don't want that.  We want a silent run.

So, on with Synaptic...

```

synaptic for Debian 0.60ubuntu5

Usage: synaptic [options]
-h   This help text
-r   Open in the repository screen
-f=? Give an alternative filter file
-t   Give an alternative main window title (e.g. hostname with `uname -n`)
-i=? Start with the initial Filter with given name
-o=? Set an arbitary configuration option, eg -o dir::cache=/tmp
** --upgrade-mode**  Call Upgrade and display changes
--dist-upgrade-mode  Call DistUpgrade and display changes
** --update-at-startup  **Call "Reload" on startup
** --non-interactive **Never prompt for user input
--task-window Open with task window
--add-cdrom Add a cdrom at startup (needs path for cdrom)
--ask-cdrom Ask for adding a cdrom and exit
--test-me-harder  Run test in a loop

```

I've bolded the Synaptic command-line switches of interest...

```

sudo synaptic --non-interactive --update-at-startup --upgrade-mode

```

...which should do the following...

1) Open Synaptic & Auto-Refresh Lists (*ok*)
2) Apply Updates Found Automatically (*problem*)

For some reason, --non-interactive mode doesn't seem to work...when updates are found, it still tosses up a pop-up asking the User to confirm the updates it found.

However, if you remove the "--upgrade-mode" part, it'll run and refresh the lists, then quit w/o any user feedback.

Now, Synaptic / Update Manager has the ability to run updates automatically & silently (Settings > Repositories > Updates) when the user is on the computer.  So, I know it can do all this without User input.  I'm just not sure how that's able to, but my CLI command can't.

Does anyone know where the hidden script is that runs silent Synaptic updates?  I'd like to look at it to see how it does it.  Or, does the silent updates use some other CLI command (aptitude?) to run silent updates?

---

### Post by bapoumba on 2007-11-21
What you are looking for is [cron-apt]("http://packages.ubuntu.com/gutsy/admin/cron-apt") and please read the following:
> Observe that this tool may be a security risk, so you should not set it to do more than necessary. Automatic upgrade of all packages is NOT recommended unless you are in full control of the package repository.

---

