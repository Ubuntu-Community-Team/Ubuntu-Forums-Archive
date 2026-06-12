---
title: "A help with troubles on sound"
date: 2023-09-02
forum: Ubuntu, Linux and OS Chat
---

### Post by beirute2 on 2023-09-02
Hey guys!
This is only my second post here on the forum ):P.
I decided to write because I found out after a lot of searching on the internet about a problem that, year after year and year after year, persists in our dear Ubuntu: sound failures, such as hissing, echo, muteness and many things...

Thanks to colleagues on the Brazilian forum (my country) I managed to solve sound problems that existed on three computers at my house and at my in-laws, in particular a hiss that echoed after the sound, something really annoying...

I don't know why but on the three computers what worked was to completely uninstall speech dispatcher, I used the command:

>  sudo apt-get remove --purge speech-dispatcher*

Although I set up this topic to help, I would like to ask a question: What is this *product* for if it only caused problems for me (at least in the last LTS 22.04 version)?

Thanks, big hug to all!

---

### Post by #&amp;thj^% on 2023-09-02
Interesting find, but to some what answer your question:
```
speech-dispatcher 0.11.5-1 (4.0 MiB 26.4 MiB) 
    High-level device independent layer for speech synthesis interface

```
And from the man page:[https://manpages.ubuntu.com/manpages/trusty/man1/speech-dispatcher.1.html](https://manpages.ubuntu.com/manpages/trusty/man1/speech-dispatcher.1.html)
```
       speech-dispatcher is a server process that is responsible for  transforming  requests  for
       text-to-speech  output  into  actual  speech  hearable  in  the  speakers.  It  arbitrates
       concurrent speech requests based on message priorities,  and  abstracts  different  speech
       synthesizers.  Client  programs,  like  screen readers or navigation software, send speech
       requests to speech-dispatcher using TCP protocol (with  the  help  of  client  libraries).
       speech-dispatcher  is  usually started automatically by client libraries (i.e. autospawn),
       so you only need to run it manually if testing/debugging, or when in other  explicit  need
       for a special setup.

OPTIONS

       -d, --run-daemon
              Run as a daemon

       -s, --run-single
              Run as single application

       -a, --spawn
              Start only if autospawn is not disabled

       -l, --log-level
              Set log level (1..5)

       -c, --communication-method
              Communication  method  to use (unix_socket or inet_socket) -S, --socket-path Socket
              path to use for 'unix_socket' method (filesystem path or 'default')

       -p, --port
              Specify a port number for 'inet_socket' method

       -P, --pid-file
              Set path to pid file

       -C, --config-dir
              Set path to configuration

       -v, --version
              Report version of this program

       -D, --debug
              Output debugging information into /tmp/.speech-dispatcher

       -h, --help
              Print this info

BUGS

       Please report bugs to <speechd-bugs@freebsoft.org>

SEE ALSO

       spd-say(1)

       The full documentation for speech-dispatcher is maintained as a Texinfo  manual.   If  the
       info and speech-dispatcher programs are properly installed at your site, the command

              info speech-dispatcher

       should give you access to the complete manual.


```

---

### Post by beirute2 on 2023-09-02
Thank you for the information @1Fallen!

But I still couldn't find a function that justifies it being installed by default lol
Probably because I don't have much expertise yet in Ubuntu ](*,)

---

### Post by #&amp;thj^% on 2023-09-03
> **beirute2 said:**
> Thank you for the information @1Fallen!

But I still couldn't find a function that justifies it being installed by default lol
Probably because I don't have much expertise yet in Ubuntu ](*,)
Gnome use's Orca see this:
```
apt depends orca
orca
  Depends: <python3:any>
    python3:i386
    python3
  Depends: gir1.2-glib-2.0
  Depends: gir1.2-gtk-3.0
  Depends: gir1.2-pango-1.0
  Depends: gir1.2-wnck-3.0
  Depends: gir1.2-gstreamer-1.0
  Depends: gstreamer1.0-plugins-good
  Depends: python3-brlapi
  Depends: python3-cairo
  Depends: python3-gi
  Depends: python3-louis
  Depends: python3-pyatspi
  Depends: python3-speechd
  Depends: speech-dispatcher
    speech-dispatcher:i386
  Depends: gsettings-desktop-schemas
  Recommends: xbrlapi
  Suggests: brltty

```
And let's peek @ speech-dispatcher
```
apt depends speech-dispatcher
speech-dispatcher
  Depends: adduser
  Depends: lsb-base (>= 3.0-10)
    sysvinit-utils:i386
    sysvinit-utils
  Depends: speech-dispatcher-audio-plugins (= 0.11.4-2ubuntu0.1)
  Depends: init-system-helpers (>= 1.52)
  Depends: libc6 (>= 2.34)
  Depends: libdotconf0 (>= 1.0.13)
  Depends: libglib2.0-0 (>= 2.75.3)
  Depends: libltdl7 (>= 2.4.7)
  Depends: libsndfile1 (>= 1.0.20)
  Depends: libspeechd2 (>= 0.9.0~rc1)
  Depends: libsystemd0
  Breaks: cl-speech-dispatcher (<< 0.9~)
  Breaks: libspeechd2 (<< 0.9~)
  Breaks: <python-speechd> (<< 0.9~)
  Breaks: python3-speechd (<< 0.9~)
  Breaks: speech-dispatcher-baratinoo (<< 0.10.2-1~)
  Breaks: <speech-dispatcher-ibmtts> (<< 0.10.2-1~)
  Breaks: speech-dispatcher-kali (<< 0.10.2-1~)
  Recommends: speech-dispatcher-espeak-ng
    speech-dispatcher-espeak-ng:i386
  Recommends: sound-icons
  Suggests: libttspico-utils
    libttspico-utils:i386
  Suggests: espeak
    espeak:i386
    espeak-ng-espeak
  Suggests: mbrola
  Suggests: speech-dispatcher-doc-cs
  Suggests: speech-dispatcher-festival
  Suggests: speech-dispatcher-cicero
    speech-dispatcher-cicero:i386
  Suggests: speech-dispatcher-flite
    speech-dispatcher-flite:i386
  Suggests: speech-dispatcher-espeak
    speech-dispatcher-espeak:i386

```
Imagine if one or more of your senses was impaired (Blind or Deaf) helps aid them.
I'm very curious if you could show links to how and where this helped in  normal sound....very curious.

---

