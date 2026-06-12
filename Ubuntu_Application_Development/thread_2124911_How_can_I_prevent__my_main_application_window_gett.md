---
title: "How can I prevent  my main application window getting black?"
date: 2013-03-12
forum: Ubuntu Application Development
---

### Post by MGTHEBOSS on 2013-03-12
I have made an ubuntu app using Quickly in Ubuntu12.04.In that app's main window there  are several buttons.
Clicking some of them opens new windows of other applications(like, firefox,gnome-sound-recorder) and clicking
some of them runs commands in the background(like, html2text,espeak ).
Suppose I have clicked a button which opens Sound Recorder.Now if I start recording in the Sound Recorder my
main application window gets black. Again when sound recording is done and I close the Sound Recorder window,
it becomes normal.
I think this part of my code is responsible for this:

[COLOR=#ff0000]os.system('gnome-sound-recorder')[/COLOR]

What statement(s) should I use instead of the abovementioned one to prevent my main application window going
black?Can someone give me some solution?

Thanks for your help in advance.

---

### Post by MGTHEBOSS on 2013-03-14
Replies:0
Views: 51

I am a beginner in Ubuntu app development.I expected that experienced developers will help
me to solve the problem.Looks like my expectation was wrong.Anyway I am trying to solve the 
problem on my own:
        [COLOR=#ff0000]child_pid = os.fork()
        if child_pid == 0:
            os.system('gnome-sound-recorder')
        else:
            return

[/COLOR][COLOR=#000000]Now, the main app window doesn't get black.
But, now if I close Sound Recorder my main
app window gets closed.

Can someone help me to solve this problem?



[/COLOR]

---

