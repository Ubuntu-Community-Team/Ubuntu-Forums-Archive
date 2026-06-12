---
title: "Edit sshd_cofig to enable audio (or more) on remote login."
date: 2011-08-23
forum: Server Platforms
---

### Post by asomad on 2011-08-23
Ok. I need sshd (thats the ssh host) to enable, or be allowed to enable audo when I log in. Once I log in to my server locally, sound is enabled as long as a local bash is active. When local bash is active, I can run command line audio operations, in various audio programs via an SSH terminal, and have the sound work at the server. 

I want the sound (device(s)?) to be active, enabled, loaded, (NOOB here) when I am ONLY logged in via SSH. I don't want to have to go to the server and log in to a local terminal to have audio loaded, this defeats the point of using SSH.. LOL sound needs to work on that server with no local login, I.e. the screen says "computername login:"

so there is something I'm missing here. Ive read over the sshd documentation many times.. Some of it is beyond my skill set, so I'm sure i'm missing something.

Or perhaps sshd needs permission to load the audio? I don't know here I'm a noob.

(I suppose I should add, this is gnome system with X disabled with the runlevel edit to gdm.conf. but audio works without starting X, so I doubt the problem lies here, as I said before the SSH connection does what I need it to as long as a local BASH (not X) session is logged in.)

---

### Post by asomad on 2011-08-25
I can add. 

Simply put, no program can access the audio via an SSH connection, UNLESS there is a local login active AT THE SERVER. , 
Maybe that's just how it is? I mean I can see why you wouldn't want your sound loaded unless you were logged into your machine locally, but in my case that's what I'd like


If you have audio in use via SSH (i.e. playing a track) and then logout of the LOCAL session AT THE SERVER, the SSH connection loses audio. the speakers go quiet.
I should add, the local login is the same username as the ssh login.... so maybe once my user is logged in locally it is THEN allowed access to sound via ssh because the user then gets more "permissions" for being logged in locally? just a thought....

I'd like to add, this problem is not dependent or related to the software being used for playback. Its ANY program. because for whatever reason, (this is exactly what i'm trying to learn), For my SSH connection to be able to load the sound device, the server must have a local login active at IT'S terminal as well. 

I can make the server auto-login perhaps. But I'd prefer not too.

If I can figure out WHY the sound only works when a local login is in session, I can move on to figuring out on my own how to make this work.

It's amusing as a noob to ask questions I need a guru to answer..Lol

---

### Post by fdrake on 2011-08-25
edit: nevermind i found out it's not that the problem.

---

### Post by asomad on 2011-08-25
i'll also add, before anyone else says it. The output of lsmod, lspci, and lspci -v, is the same, on the ssh terminal regardless of a local login at the server. additionally, the outputs are identical at the servers terminal as well...

so everything is in place for the sound to work via SSH, (and it does), but only when I have a local login active.

this is why I keep hitting a dead end.... lol

something keeps the sound from being accessed... hmmm

---

### Post by fdrake on 2011-08-25
> **asomad said:**
> i'll also add, before anyone else says it. The output of lsmod, lspci, and lspci -v, is the same, on the ssh terminal regardless of a local login at the server. additionally, the outputs are identical at the servers terminal as well...

so everything is in place for the sound to work via SSH, (and it does), but only when I have a local login active.

this is why I keep hitting a dead end.... lol

something keeps the sound from being accessed... hmmm

it must be somthing with the session's enviorments

the variable in ssh are less than when you are locally logged

```

env | less

```


maybe looking at the way pulse starts may help:

```

less /etc/rc5.d/S50pulseaudio
..........
pulseaudio_start () {
        log_daemon_msg "Starting system PulseAudio Daemon"
        if [ ! -d $PIDDIR ]; then
                mkdir -p $PIDDIR
                chown $DAEMONUSER:$DAEMONUSER $PIDDIR
        fi
        start-stop-daemon -x $DAEMON -p $PIDFILE --start -- --system --daemonize --high-priority --log-target=syslog --disallow-module-loading=$DISALLOW_MODULE_LOADING
        status=$?
        if [ -e /var/run/pulse/.esd_auth ]; then
                chown pulse:pulse-access /var/run/pulse/.esd_auth
                chmod 640 /var/run/pulse/.esd_auth
        fi
        if [ -e /var/run/pulse/.pulse-cookie ]; then
                chown pulse:pulse-access /var/run/pulse/.pulse-cookie
                chmod 640 /var/run/pulse/.pulse-cookie
        fi
        log_end_msg ${status}
}

..........

```

---

### Post by asomad on 2011-08-25
:-)

im glad you and me are on the same page. Cause I just spent the last hour looking into pulseaudio settings... and I come back here and your thinking the same thing! I think the answer lies there my friend... 

running as a system instance doesnt help. daemonizing it doesnt help. no matter what I only have sound when a local login is active. And env output is IDENTICAL at the server's terminal AND at the SSH terminal, looked into that early on (however I am a n00b and I wouldnt know if there is more variables than what is listed with "env" or "printenv")..

So it's time for me to figure out how to get pulseaudio to allow my ssh terminal to play sound from the server, without me being logged into the server locally.


[SOLVED]


By default (I think), the only user in group "audio" is "pulse".

adding your username to the group: audio, allows your user access to the  servers sound via a SSH connection, without a local login...

thanks to everyone for the help and direction.

---

