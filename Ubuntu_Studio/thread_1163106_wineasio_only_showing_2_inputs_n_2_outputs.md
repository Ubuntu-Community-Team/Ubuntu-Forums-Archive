---
title: "wineasio only showing 2 inputs n 2 outputs"
date: 2009-05-18
forum: Ubuntu Studio
---

### Post by fedexnman on 2009-05-18
i have a 6 in out firewire interface, and when running reaper it only shows 2 inputs n 2 outputs, its not showing 6 in n outs. anybody know how to fix this ??  (ardour shows all my inputs n outputs)

---

### Post by thorgal on 2009-05-18
sure :)

in the source code, there's a file called settings.h

in particular, there are two constant defines:

```

static const int   DEFAULT_NUMINPUTS = 2;
static const int   DEFAULT_NUMOUTPUTS = 2;

```

so if you grab the source code, modify them to what you want, recompile and reinstall. And probably re-register it (regsvr32 /usr/local/lib/wine/wineasio.dll.so or /usr/lib/wine/wineasio.dll.so depending on where you installed it).


EDIT: ah wait a second! looking at the code, I can see wineasio can use a configuration file, either a user one in $HOME/.wineasiocfg or a system one in /etc/default/wineasiocfg
Let me look what kind of format it is supposed to hold. It is a text file for sure ... hang on ...


EDIT 2: OK, it's all in teh README.txt file

You create a $HOME/.wineasiocfg (use your favorite text editor). Then follow these instructions (from the README file):

```

2. USER INSTRUCTIONS
--------------------

The driver can be configured in two ways: either using environment variables or
using a configuration file.

The configuration file can be set per user in ".wineasiocfg".  As a fallback, a
site-wide file can be provided in "/etc/default/wineasiocfg" if desired.

The format for the configuration file is simply "var=val".

If using the shell, either include the assignment on the command line:
    ASIO_INPUTS=0 ~/bin/reaper.exe
or ensure the variable has been exported:
    export ASIO_INPUTS=0
    ~/bin/reaper.exe

The available variables are as follows:
ASIO_INPUTS
ASIO_OUTPUTS
ASIO_INPORTNAME<n>
ASIO_OUTPORTNAME<n>
ASIO_INPORT<n>
ASIO_OUTPORT<n>
<clientname>

The last entry allows you to change the client name from the default, which is
constructed from the program name prefixed by "ASIO_".  For example,
    ASIO_reaper=REAPER
All of the entries beginning ASIO_ can also have entries specific to a client,
using the assigned client name.  For example,
    ASIO_reaper_INPUTS=0
or (if the client name has been re-assigned as above),
    REAPER_INPUTS=0

INPUTS and OUTPUTS
------------------
These let you limit the number of JACK ports allocated to this client.  The
default value for both is 2.

INPORTNAME and OUTPORTNAME
--------------------------
These allow you to rename the input and output ports for the client.  The
default names are "input_<n>" and "output_<n>".  For example,
    REAPER_OUTPORTNAME0=left
    REAPER_OUTPORTNAME1=right

INPORT and OUTPORT
------------------
These allow you to connect the client to JACK ports of your choice.  The
default is to connect JACK's "hardware" inputs to your client's inputs and your
client's outputs to JACK's "hardware" outputs.  You might be running some other
application, e.g. an icecast server, and want to send output to that.  For
example,
    ASIO_OUTPORT0=idjc-mx:aux_lt
    ASIO_OUTPORT1=idjc-mx:aux_rt

```

---

### Post by fedexnman on 2009-05-18
thx , i installed wineasio.dll.so  that i got  from www . sandgreen . dk  and i used nautilis to install  the dll in lib32 in wine. everything works but im missing 4 of my imports.   so i guess i go in a file somewhere n edit these numbers ?  hitting a brick, but im gonna learn it !

---

### Post by thorgal on 2009-05-19
just follow the instructions I copy/pasted (titled USER INSTRUCTIONS):

edit a file called $HOME/.wineasiocfg

add wineasio variables containing the number of ins and outs as described in my previous post.

You can even customize for specific applications (like 6 IOs for reapers, 2 for whatnot, etc).

---

