---
title: "Avast is Missing Context Menu for Individual or Groups of Files?"
date: 2011-10-23
forum: Security
---

### Post by northd_tech on 2011-10-23
I'm posting this to see/clarify if anyone knows of a shell script or workaround for the apparent lack of a 'Right Click' Context Menu to "scan with avast" for single or groups of files from the** avastgui**.

I did find a workaround that will do single or groups of files though using the command line **avast**.  Open a terminal and navigate to the directory that has the file(s) to be virus scanned, then execute the following command with appropriate wildcards:
[COLOR=Blue][B]
Example 1[/B][/COLOR]
```
avast ./*.html
```Virus scans all **.html** files in the current subdirectory- this is the output that I got when running it in my Documents directory for testing (and all the .**html** files scanned clean):
> #
# Statistics:
#
# scanned files:     37
# scanned directories:     0
# infected files:     0
# total file size:     1.9 MB
# virus database:     111022-1 22.10.2011
# test elapsed:     0s 451ms
#
[COLOR=Blue]**Example 2**[/COLOR]
```
avast C*.exe
```Scans all **.exe** files that start with a Capital 'C' in the current directory.

[COLOR=Blue]**Example 3**[/COLOR]
```
avast foobar.zip
```Scans the single .zip file "foobar.zip."

Of course, a simple **avast **with no parameters will scan your Home directory by default.

Also, the most current version of Avast for Linux that I found (1.4.0) was at the link below (and I just **gksu nautilus** copied the files into the appropriate locations in **/bin/**, **/lib/**avast4workstation/, and **/usr/share/**... for the manual pages/documents (which I'm still trying to straighten out).  My 64-bit Lucid Lynx 10.04.3 LTS did NOT like the 32-bit i386.deb file when I briefly *attempted* to install Avast Antivirus that way (since no 64-bit Avast could be found anywhere, and I'm not too impressed with ClamAV/ClamTk).

Lastest avast4 workstation - test it :) 
[http://forum.avast.com/index.php?topic=45237.0](http://forum.avast.com/index.php?topic=45237.0)

I hope this helps someone, and if a PERL guru wants to attempt scripting a 'context menu' of sorts to scan single (or maybe selectable groups also) files, that would be greatly appreciated- my scripting skills are very rusty...

For reference, here is the output of the Avast help command switch:

**avast -h**
> Usage: avast [OPTION...] <areaname...>
avast v1.4.0 -- command-line virus scanner

Options:
  -_, --console              Application will be working in STDIN/STDOUT mode
  -a, --testall              Test all of the files (default)
  -b, --blockdevices         Scan block devices
  -c, --testfull             Scan entire files
  -d, --directory            Scan only directory content, no subdirectoires
  -i, --ignoretype           Ignore virus sets
  -n, --nostats              No virus check statistics
  -p, --continue=1234        Automatic action with infected file:
                             1:delete, 2: (not supported), 3:repair, 4:stop
  -r, --report=
[*]file       Create report file, '*' for OK results
  -t, --archivetype[=ZGBTIJRXOQHFVKPYD6UCWAN]  Scan archives: Z:ZIP(default),
                             G:GZ(default), B:BZIP2(default), T:TAR(default),
                             I:MIME, J:ARJ, R:RAR, X:Exec(default), O:ZOO,
                             Q:ARC, H:LHA, F:TNEF, V:CPIO, K:CHM, P:RPM,
                             Y:ISO, D: DBX, 6:SIS, U:OLE(default), C:CAB,
                             E:ACE, 1:INSTALL(default), W:WINEXEC(default),
                             A:All, N:None
  -v, --viruslist=mask       Show list of all specific viruses
  -h, --help                 Give this help list
      --usage                Give a short usage message
  -V, --version              Print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

---

### Post by northd_tech on 2011-10-23
Apparently, there has been a "scan with Avast" context request since about July 2008.  Here is a relevant thread at the Avast forum:

**[[B]Avast Mac "Scan this file with avast" context**]("http://forum.avast.com/index.php?topic=37295.msg312335#msg312335")[/B]
[http://forum.avast.com/index.php?topic=37295.0](http://forum.avast.com/index.php?topic=37295.0)

Hopefully, this will be addressed in the LONG-awaited Avast 5 (1.5.0) Linux version.

---

### Post by northd_tech on 2011-11-11
If you are getting an error message involving "Avast! Error: An error occurred in avast! engine: Invalid argument" when trying to start the **avastgui** or the command line **avast**, see post #63 here:

[http://ubuntuforums.org/showpost.php?p=11447817&postcount=63](http://ubuntuforums.org/showpost.php?p=11447817&postcount=63)

---

