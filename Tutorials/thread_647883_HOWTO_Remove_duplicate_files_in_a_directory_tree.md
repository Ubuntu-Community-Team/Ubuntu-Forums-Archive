---
title: "HOWTO: Remove duplicate files in a directory tree"
date: 2007-12-22
forum: Tutorials
---

### Post by penguin007 on 2007-12-22
I recently had to merge an old backup onto a new drive, and of course ended up with a large number of duplicate files scattered all over the new drive. By digging around, I discovered the program "fdupes" which will run through a directory tree and find all the duplicates by calculating the MD5 checksums and comparing these. This is great, as it means that even if the file names are different, it will find it. It even has a -d switch, which will ask you which file to keep and which to delete.

However...... with roughly 12,000 duplicates in my directory tree, I was not going to sit there and answer the same question 12,000 times. So I wrote a little Python program to do the dirty work.

Here's what I did, after installing fdupes via Synaptic:

```
fdupes -r /home/top_dir > xdupes.txt
```

This will run through the directory tree starting at top_dir and output its results into the file xdupes.txt.

Next, I ran this little Python program:

```
import sys
text_file=open("xdupes.txt","r")
lines=text_file.readlines()
text_file.close()
text_file=open("xdupes_rm.sh","w")
my_count=len(lines)

for i in range(my_count):
	next_count = i + 1
	if next_count == my_count:
		sys.exit()				# escape hatch
	else:
		if len(lines[next_count]) > 1:		# next line is not blank, so rm this line
			out_line1 = lines[i].rstrip()	# remove trailing \n
			out_line = 'rm ' + '"' + out_line1 + '"' + '\n'
							#add a \n after the closing quote
			if len (out_line) > 6:		# don't write out rm ""\n, Nigel!
				text_file.write(out_line)

text_file.close()


```

This then creates an output file named "xdupes_rm.sh" that contains all the duplicate file names read in from "xdupes.txt", except the LAST name. For example, if fdupes has found files A, B, and C to be the same, then the file names A and B will be written to "xdupes_rm.sh".

Next, make it executable:

```
chmod 777 xdupes_rm.sh
```

If you are unsure, use a text editor to check xdupes_rm.sh and xdupes.txt, and check that not all files will be removed.

Now run the removal script:

```
./xdupes_rm.sh
```

Note: With a large number of files it can take a LONG time. Fortunately, fdupes five you visual feedback, so you know it's working.

---

### Post by carpman on 2008-01-03
Hello, been trying to use you suggestion but can get the python script to work?

> 
./fdupes-batch.py
./fdupes-batch.py: line 1: import: command not found
./fdupes-batch.py: line 2: syntax error near unexpected token `('
./fdupes-batch.py: line 2: `text_file=open("xdupes.txt","r")'



Would love to get it working as have 14000+ dup email to sort out.

I created file fdupes-batch.py with you python script and chmod it 777.


many thanks

---

### Post by jotka on 2008-04-15
Thanks, works fine for me out of the box.
@ carpman: python fdupes-batch.py, not sh fdupes-batch.py

---

### Post by phissure on 2008-06-03
After some experimentation, I found a nice one-line command.
Let's say your working directory is "abunchoffiles" and your setup looks like this:

/home/
/home/abunchoffiles/
/home/duplicates/

```
fdupes -fr . | xargs mv  -t ../duplicates 
```

Using the above code, you can move all the duplicate files (recursively) into the directory "duplicates."  I find this much safer (mentally, at least) than rm-ing them.
I have run into a small problem with escape characters ($,(,), etc), but I imagine there's some way around it.  I just haven't figured it out yet...

---

### Post by chill on 2008-06-04
Hi,

Does anyone know a graphical tool to remove duplicate photos under Ubuntu?

Thanks,

---

### Post by penguin007 on 2008-07-02
You have to run it as a Python script:

>python fdupes-batch.py

---

### Post by spider_0k on 2008-08-03
A little late for you Chill, I'm sure, but for the rest of you here looking for the answer. Fslint is a duplicate file finder, with a nice GUI, and its in our repositories. [http://ndblocks.com/index.php?hl=f5&q=uggc%3A%2F%2Fhohagh.jbeqcerff.pbz%2F2005%2F10%2F08%2Fsvaq-qhcyvpngr-pbcvrf-bs-svyrf%2F]("http://ndblocks.com/index.php?hl=f5&q=uggc%3A%2F%2Fhohagh.jbeqcerff.pbz%2F2005%2F10%2F08%2Fsvaq-qhcyvpngr-pbcvrf-bs-svyrf%2F")

The link has a good description and howto. I used it on my ebboks folder, I found I had ten copies of some books! Hope this helps you too.

Philip

---

### Post by Anlace on 2008-08-21
Spider,

I would really like to see that link to a good description and howto for FSlint.  I can see that FSlint is a powerful program but it is anything but intuitive to use.  The help pages and MAN file are so vague as to be useless.

Anyway, enough rant, when I navigate to your link I get:

> NDBlocks
Resource Error: An error has occured while trying to browse through the proxy.
It appears that you are trying to access a resource through this proxy from a remote Website.
For security reasons, please use the form below to do so.

So if you have that link still and can provide it that would be fabulous! ;)

---

### Post by spider_0k on 2008-08-22
Firstly, sorry. Very bad of me not to check my post before submission. I am based in China so I often have to use a proxy (Firefox, Gladder extension) to get around even "normal" web sites. I had to search again 
for the links :(:oops: 

[http://www.ubuntugeek.com/fslint-toolkit-to-fix-various-problems-with-filesystems-data.html]("http://www.ubuntugeek.com/fslint-toolkit-to-fix-various-problems-with-filesystems-data.html")

Ubuntu Geeks have a reasonable guide. That was the one I followed.

If you needs are pretty straight forward but you need some visual confirmation first (after all deleting is the scariest thing), then this is the app for you.

As I said I didn't do anything 'special', but if you feel the need for more help .......

---

### Post by Nemo_bis on 2010-01-01
Fdupes and FSlint are useless if your duplicates are not identical: see [Robust image duplicate finder](http://ubuntuforums.org/showpost.php?p=8594282&postcount=2); I found GQview to be the best tool.

---

### Post by hgghfnvk on 2010-02-02
> **Nemo_bis said:**
> Fdupes and FSlint are useless if your duplicates are not identical

If your duplicates are not identical then they're not duplicates...

---

### Post by airtonix on 2010-02-12
> **hgghfnvk said:**
> If your duplicates are not identical then they're not duplicates...

To be pedantic, this is true.

However : 

> 1. [ The red rabbit cackled manically as the blufox lept into oncoming traffic ]

2. [ THE RED RABBIT CACKLED MANICALLY AS THE BLUFOX LEPT INTO ONCOMING TRAFFIC ]

3. THE RED RABBIT CACKLED MANICALLY AS THE BLUFOX LEPT INTO ONCOMING TRAFFIC

4. The red rabbit cackled manically as the blufox lept into oncoming traffic


Despite their appearance, the above four phrases are obviously all identical in meaning... They all convey the exact same lexical concept.

This concept in the context of images, means that fslint and fdupes will not help you find extreme similarities.

---

### Post by topher5 on 2010-02-16
Ran across this thread today while trying to do this exact thing.  Looking at the man page for fdupes it looks like you can delete duplicates all in one command.  Per the man page if you want to actually be prompted each time just remove the --noprompt option.

 fdupes -r --delete --noprompt <dir>

---

### Post by Thad E Ginathom on 2011-02-26
**Thank you** to this thread and its contributors.

fslint worked well for me, finding nearly 300 duplicates in over 14Gb of 6,725 files in minutes --- I was prepared for it to take hours. 

My photos are sorted. Now to deal with music and other areas!

---

### Post by Hilko on 2011-03-19
Thanks. I found both fdupes and fslint very usefull. However they did not find all the duplicates. I had a number of identical photos, because F-spot imported them again and did not detect them as duplicate. But these were not found by fdupes.
I knew they had very similar filenames like 'nameOfphoto.jpg' and 'NameOfphoto-1.jpg'. So I did
```
ls -R Photos/ | tee listOfPhotos.txt
```
and then after playing with egrep I managed to find a lot more duplicates.

---

### Post by antiplex on 2011-10-26
hi,

trying to solve a similar issue i found the scripts provided by penguin007 quite useful and modified/extended it a bit e.g. the first match of a duplicate file (duplicate in terms of same hash as determined by fdupes) is kept and the following duplicates are removed.
furthermore, after removing the duplicates the script offers to remove all empty folders.
and the python-script requires to provide a parameter containing the file with the fdupes output.

maybe this is helpful to some of you as well, so either copy&paste below code into a .py file or download the attached file.
```
#!/usr/bin/env python

""" process output of fdupes by removing duplicate files and empty folders
    note that the first occurrance of each file that had duplicates detected will be kept while all following
    absolutely no guarantee is taken for any loss of data or any other misbehaviour that might occur, use this at your own risk!
    be careful if your filenames contain caracters with special functions within bash and free your files from these characters
    if so e.g. by issuing a find -type f -iname '*`*' -exec rename 'y/\`/_/' {} \; (this would replace '`' with a harmless '_'


    created by antiplex (antiplex@coma.cc)
    version 0.2.1 (2011-10-24)
    inspired by the code-snippet of penguin007 in this thread: [http://ubuntuforums.org/showthread.php?t=647883](http://ubuntuforums.org/showthread.php?t=647883)
    distributed under the terms of the MIT-license model, for details see htt://coma.cc/license/mit.html
"""

import os
import exceptions
import sys
import stat

## global var intitialization
dupeListFile = ''  # source file containing fdupes output
dupeRmScriptTarget = 'zzz_rmDupes.sh' # target script file to create


""" print usage info and exit """
def prntusg():
  print 'usage: %s <fdupesLogFileToRead>' % os.path.basename(sys.argv[0])
  sys.exit(4)

""" read fdupe output from file specified in arg#1 and generate a bash-script that removes all but the first dupe """
def main(argv=None):
  if argv is None:
    argv = sys.argv

  ## check command params
  if len(argv) < 2:
    prntusg()
  elif not os.path.isfile(argv[1]):
    print 'could not find file %s!' % argv[1]
    sys.exit(5)
  else:
    dupeListFile = argv[1]

  try:
    dupeListFH = open(dupeListFile,'r')
    dupeListLines = dupeListFH.readlines()
    dupeListLinesLength = len(dupeListLines)
    dupeListFH.close()
    rmDupeScriptFH = open(dupeRmScriptTarget,'w')
    rmDupeScriptFH.write('#!/bin/bash\n\n## this is a script for duplicate file removal generated by %s\n\nrmCount=0\n\necho -n "removing duplicate files..."\n\n' % os.path.basename(argv[0]) )  # add header to shellscript

    for i in range(dupeListLinesLength):
      nextCount = i + 1
      if nextCount == dupeListLinesLength:  # end of list reached?
        print 'successfully processed %d lines of %s' % (dupeListLinesLength, dupeListFile)
      elif len(dupeListLines[i].strip()) and len(dupeListLines[nextCount].strip()):   # current line and next line are not blank
        outline = 'rm "%s" && rmCount=$(($rmCount+1))\n' % (dupeListLines[nextCount].rstrip())
        rmDupeScriptFH.write(outline)
        ## debug output
        #print 'wrote statement >>%s<< to %s.' % (outline.strip(), dupeRmScriptTarget)

    rmEmptyDirsSH = """
echo " done - removed ${rmCount} files."

# ask to remove all remaining empty folders if run interactively
if [[ -z "${PS1+isThisVarDefined}" ]] ; then
  echo ""
  echo -n "remove all empty dirs? [y|N] " 
  read proceed
else
  proceed="nonInteractive"
fi

if [[ "$proceed" == "y" || "$proceed" == "Y" ]] ; then
  find -type d -empty -delete
  ## with older find versions this should be used instead
  #find -depth -type d -empty -exec rmdir {} \;
  execStat=$?
  if [[ ${execStat} -ne 0 ]]; then
    echo "emptyfolder-removescript returned with an error, please check manually!"
  else
    echo "empty folders removed."
  fi
else
  if [[ "$proceed" == "nonInteractive" ]] ; then
    echo "not removing empty folders since not running interactively!"
  else
    echo "not removing any empty folders."
  fi
fi"""

    rmDupeScriptFH.write(rmEmptyDirsSH)

    ## debug
    #print 'mod is %d' % int(stat.S_IRUSR | stat.S_IWUSR | stat.S_IXUSR)

    ## weird, this does give an error 'integer expected'
    #os.fchmod(rmDupeScriptFH, int(stat.S_IRUSR | stat.S_IWUSR | stat.S_IXUSR)) # set mode 700 to script (make executable for user)
    rmDupeScriptFH.close()
    os.chmod(dupeRmScriptTarget, int(stat.S_IRUSR | stat.S_IWUSR | stat.S_IXUSR)) # set mode 700 to file (make executable for user)
    print 'generated script %s, execute it to start deletion of duplicate files and empty folders.' % dupeRmScriptTarget
  except StandardError as e:
    print 'caught exception %s' % e
    return 3


""" execute main-function if directly executed """
if __name__ == "__main__":
  sys.exit(main() or 0)  # forward exit status returned from main()


```

---

### Post by AdmiralMorketh on 2012-02-09
First off i want to Thank penguin007 for the python script which i have mutilated and reworked for a cleaner approach to the problem of duplicate data. also taking into consideration a "peace of mind" approach from phissure i have now eliminated the need for *.SH scripts to call the python script the reworked script at this point still provides an annoying error saying: ```
mv: missing destination file operand after `/home/xdupes/'
``` how ever im sure with a bit more tweaking that can be fixed i use this on a regular basis maintaining several servers and backup directories with data ranging in the Tera-bytes the new script posted below and attached to the document removes empty folders and it takes into account the Current Working Directory so you don't have to copy the script all over your file system to use it all you need to do is add it to /etc/profile if you want every user to be able to use it:
```
PATH=$PATH:/usr/scripts/
export PATH
```Im sure there is an easer way to do that anyway heres the updated script once again thank you to Penguin007 & Phissure for the ideas and the basic script no more duplicate data and clean server ^_^
```
#!/usr/bin/env python
import sys
sys.path.insert(0, "os")
import os
from subprocess import call
import re

call("clear",shell=True)                        # clear the shell before we start
cwd=os.getcwd()

# replace all " " with "\ " this escapes ONLY the spaced names not anything else
cwd_e=cwd.replace(" ","\ ")


print "Current Directory is:" + cwd

dup_dir=cwd_e+"/xdupes"                            # define dupe_dir for ease of use for moving stuff
call("mkdir "+dup_dir,shell=True)                     # create a duplicate dump folder



options=" -r %s > xdupes.txt" % (cwd_e)                    # fdupes options and output file name xdupes.txt in Curent Working Dir
call("fdupes" + options, shell=True)                    # call fdupes with formated option string

text_file=open(cwd+"/xdupes.txt","r")                    # open CWD/xdupes.txt in read mode
lines=text_file.readlines()                        # count lines
text_file.close()                            

my_count=len(lines)                            # inform user of how many duplicates found not acurate at all this countss empty lines in the file
print "Total duplicates found: %s" % (my_count) 

for i in range(my_count):
    next_count = i + 1
    if next_count == my_count:
        print "All Files Moved"
    else:
        if len(lines[next_count]) > 1:                # next line is not blank, so rm this line
            out_line1 = lines[i].rstrip()            # remove trailing \n
            outfile_list=out_line1.split("/")        # ParseString2List '/' is the seperator
            outfile=outfile_list[-1]            # get the last item in the list
            outfile=dup_dir+"/"+re.escape(outfile)
            out_line = "mv -f %s %s" % (re.escape(out_line1), outfile)     # format string for call() to dump everything to the duplicate dump folder
            if len (out_line) > 6:                # don't write out mv ""\n, Nigel! theres a bug in this now that we are using CWD
                call(out_line,shell=True)        # call function
#                print "moving file: %s to %s" % (re.escape(out_line1), outfile)

# clean up tmp files
print "Establishing File Link: cleaning up duplicate mess"
call("rm "+cwd_e+"/xdupes.txt",shell=True)
print "TMP files removed now cleaning up empty folders"
call("find -type d -empty -delete",shell=True)
```

---

### Post by ToshibaLaptoplinux on 2012-02-24
> **phissure said:**
> After some experimentation, I found a nice one-line command.
Let's say your working directory is "abunchoffiles" and your setup looks like this:

/home/
/home/abunchoffiles/
/home/duplicates/

```
fdupes -fr . | xargs mv  -t ../duplicates 
```

Using the above code, you can move all the duplicate files (recursively) into the directory "duplicates."  I find this much safer (mentally, at least) than rm-ing them.
I have run into a small problem with escape characters ($,(,), etc), but I imagine there's some way around it.  I just haven't figured it out yet...

I would like to execute this command you provided and burn the dupes onto a DVD just to be safe. Yes I am paranoid about losing data. Haha.

Did you or anyone else find a way to workaround the escape character issue? Also, I have files that have non Roman characters as well (Japanese). Will they present a problem if running this command?

---

