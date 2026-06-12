---
title: "HOWTO download from FileSonic via a Python script"
date: 2011-03-08
forum: Tutorials
---

### Post by rrwood on 2011-03-08
Here's a Python script to make it easy to download files from Filesonic via the command line (i.e. no need for a GUI download manager).  Just replace the userid, password, and dataURLs with the appropriate values and run the script.  Note that the dataURLs can be multiple lines of URLs.

I just run the script as "python fs_get.py", but you might prefer to add the necessary bits to make it directly executable (add the usual "#!/usr/bin/python" at the start and the "#if __name__ == "__main__":" junk at the bottom).

Obviously there are lots of small things that could be done to make this nicer, so go wild and post your changes to this thread.  For me, it works well enough as-is.


```

import cookielib, urllib2, urllib
import re
import sys, os, traceback
import logging
import time


userid = "YOUR.USERID@EMAIL.WHEREVER"
password = "SEEEEEKRIT"

loginURL = "http://www.filesonic.com/user/login"

dataURLs = """
http://www.filesonic.com/file/151801321/US_TDY_2011-03-02.rar
"""





def dump_cookies(cookieJar):
	# Print out the HTTP cookies in a CookieJar object
	#
	# cookieJar = a CookieJar object to dump
	
	logging.debug("Cookies:")

	for c in cookieJar:
		logging.debug("%s = '%s'", c.name, c.value)


def login_filesonic(userid, password):
	# Log-in to Filesonic by passing the userid/password and storing the resulting auth cookie
	#
	# userid = filesonic account userid
	# password = filesonic account password
	#
	# returns an urllib2.OpenerDirector object


	logging.debug("Preparing login data...")

	loginData = dict()
	loginData["email"] = userid
	loginData["redirect"] = "/"
	loginData["password"] = password
	loginData["rememberMe"] = "1"
	

	encodedLoginData = urllib.urlencode(loginData)

	logging.debug("Generated encoded login data = '%s'", encodedLoginData)


	logging.debug("Creating urllib2 opener...")

	cookieJar = cookielib.CookieJar()
	opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookieJar))


	logging.info("Opening login URL, '%s'...", loginURL)

	page = opener.open(loginURL, encodedLoginData)

	dump_cookies(cookieJar)

	return opener



def byteSizeString(byteCount):
	# Format a data count in a convenient human-readable form-- i.e. as X.XX GB, X.XX MB, X.XX kB, or X bytes
	#
	# byteCount = number of bytes of data
	#
	# returns the formatted string
	
	if (byteCount > 1024*1024*1024):
		return "%.2f GB" % (float(byteCount) / float(1024*1024*1024))
	elif (byteCount > 1024*1024):
		return "%.2f MB" % (float(byteCount) / float(1024*1024))
	elif (byteCount > 1024):
		return "%.2f kB" % (float(byteCount) / float(1024))
	else:
		return "%d bytes" % (byteCount)


def timeString(seconds):
	# Format a time in a convenient human-readable form-- i.e. as H:MM:SS, M:SS, S sec
	#
	# seconds = number of seconds
	#
	# returns the formatted string
	
	timeStr = ""
	seconds = int(seconds)
	hours = int(seconds / (60*60))
	seconds -= hours * 60*60
	mins = int(seconds / 60)
	seconds -= mins * 60

	if (hours > 0):
		timeStr = "%d:%02d:%02d" % (hours, mins, seconds)
	elif (mins > 0):
		timeStr = "%d:%02d" % (mins, seconds)
	else:
		timeStr = "%d sec" % (seconds)

	return timeStr


def dump_headers(headers):
	# Log a list of headers
	#
	# headers = the list of headers to log (presumably from a mimetools.Message object returned by the info() method of a ulrlib2.open() response object)
	
	logging.debug("Headers:")

	for i,h in enumerate(headers):
		while (h[-1] == '\n' or h[-1] == '\r'):
			h = h[:-1]
		logging.debug("%d: %s" % (i,h))


		
def fetch_data_URL(opener, dataURL):
	# Retrieve and save a Hotfile data URL.  File is saved in the current directory, named according to the filename returned by Hotfile.
	#
	# opener = an urllib2.OpenerDirector object with an authorization cookie in the contained CookieJar
	# dataURL = the hotfile URL to fetch
	
	logging.info("Fetching data page '%s'...", dataURL)

	page = opener.open(dataURL)

	logging.debug("Response URL = '%s'", page.geturl())

	logging.info("Successfully received headers; processing...")
	metadata = page.info()
	dump_headers(metadata.headers)

	
	# Check the returned headers; this could throw an exception if Content-Length or Content-Disposition are missing
	# If the headers are not as expected, the file has probably been removed from Hotfile
	
	contentType = metadata.getheader("Content-Type")
	contentTransferEncoding = metadata.getheader("Content-Transfer-Encoding")
	contentDisposition = metadata.getheader("Content-Disposition")
	contentLength = int(metadata.getheader("Content-Length"))
	matches = re.search(r'filename="(.+)"', contentDisposition)
	filename = matches.group(1)

	logging.debug("Content Type = %s", contentType)
	logging.debug("Content Length = %s", contentLength)
	logging.debug("Content Transfer Encoding = %s", contentTransferEncoding)
	logging.debug("Content Disposition = %s", contentDisposition)
	logging.debug("filename = %s", filename)
	
	if (contentType[0] == '"' and contentType[-1] == '"'):
		contentType = contentType[1:-1]
		logging.debug("Trimmed Content Type = %s", contentType)

	if (contentType != "application/octet-stream"):
		logging.error("Unknown content type, '%s'; skipping URL", contentType)
		raise Exception("Unknown content type, '%s'" % (contentType))

	if (contentTransferEncoding != "binary" and contentTransferEncoding != None):
		logging.error("Unknown transfer encoding, '%s'; skipping URL", contentTransferEncoding)
		raise Exception("Unknown transfer encoding, '%s'" % (contentTransferEncoding))



	logging.info("Opening output data file, '%s'...", filename)

	dataFile = open(filename, "wb")


	logging.info("Fetching %d bytes of data...", contentLength)

	# We print a lot of progress info, which requires a lot of state variables...
	
	rateTuples = [ ]
	startTime = time.time()
	prevTimeInt = int(startTime)
	bytesRead = 0

	avgRate = 0.0
	
	currentRateStr = "0.0 kB/s"
	overallRateStr = "0.0 kB/s"

	totalTimeStr = "0sec"
	timeLeftStr = "0sec"

	contentLengthStr = byteSizeString(contentLength)
	
	prevStatusLineLength = 0

	while (bytesRead < contentLength):
		# Read and save the next chunk of bytes
		
		byteCount = 16384
		
		if (contentLength - bytesRead < byteCount):
			byteCount = contentLength - bytesRead

		dataChunk = page.read(byteCount)
		dataFile.write(dataChunk)
		bytesRead += len(dataChunk)
		bytesReadStr = byteSizeString(bytesRead)
		percentCompleteStr = "%.1f" % (float(bytesRead * 100.0) / contentLength)
		
		
		# Calculate elapsed time; only recalc the download rates once per second
		
		currentTime = time.time()
		currentTimeInt = int(currentTime)

		if (currentTimeInt > prevTimeInt):
			# Maintain a window of the last 10 seconds
			if (len(rateTuples) >= 10):
				del rateTuples[0]
			timeTuple = (currentTimeInt, bytesRead)
			rateTuples.append(timeTuple)

			prevTimeInt = currentTimeInt

			if (len(rateTuples) >= 2):
				first = rateTuples[0]
				last = rateTuples[-1]
	
				timeDelta = last[0] - first[0]
				byteDelta = last[1] - first[1]
	
				avgRate = float(byteDelta) / float(timeDelta)
				currentRateStr = "%.2f kB/s" % (float(avgRate) / 1024.0)

		
		# How much data is left to read?
		
		bytesLeft = contentLength - bytesRead
		
		if (avgRate > 0.0):
			timeLeft = int(bytesLeft / avgRate)
			timeLeftStr = timeString(timeLeft)

		totalTime = currentTime - startTime
		totalTimeStr = timeString(totalTime)

		if (totalTime > 0):
			overallRate = (float(bytesRead) / 1024.0) / totalTime
			overallRateStr = "%.2f kB/s" % (overallRate)
		
		# Format and print the status line, taking care to erase junk at the end if necessary
		
		statusLine = "Read %s / %s = %s%% ; current rate = %s, overall rate = %s; elapsed time = %s, time remaining = %s" % (bytesReadStr, contentLengthStr, percentCompleteStr, currentRateStr, overallRateStr, totalTimeStr, timeLeftStr)
		newStatusLineLength = len(statusLine)
		
		if (newStatusLineLength < prevStatusLineLength):
			statusLine += " "*(prevStatusLineLength - newStatusLineLength)
		
		prevStatusLineLength = newStatusLineLength
		
		print "\r",statusLine,
		sys.stdout.flush()

	print

	logging.info("Closing data file....")
	
	dataFile.flush()
	os.fsync(dataFile)
	dataFile.close()




#logging.getLogger().setLevel(logging.DEBUG)
logging.getLogger().setLevel(logging.INFO)

opener = login_filesonic(userid, password)

for l in dataURLs.splitlines():
	if (len(l) > 0):
		logging.info("Processing URL '%s'", l)

		try:
			fetch_data_URL(opener, l)
			#print "pass...."
			
		except KeyboardInterrupt:
			logging.error("Caught KeyboardInterrupt exception; halting....")
			break
		except:
			exceptionType = str(sys.exc_info()[0])
			exceptionValue = str(sys.exc_info()[1])
			exceptionTrace = traceback.format_exc()
			logging.error("An exception occurred while fetching URL '%s'", l)
			logging.error("Exception type = %s", exceptionType)
			logging.error("Exception value = %s", exceptionValue)
			logging.error("Exception trace = %s", exceptionTrace)

			logging.error("Skipping URL, '%s'.", l)

		logging.info("----------------------------------")

print "Exiting."

```

---

### Post by titansking on 2011-04-15
Does it use wget? Or its own download method? 

Is it possible to make this script use wget instead for the actual download part?

---

### Post by rrwood on 2011-04-15
The exception you mentioned at first occurs when the file has been removed from Filesonic.  Try accessing the file via a browser and you should see some note to that effect.

Using wget would make sense from a bash script.  You could technically also call it from a Python script, but it would be a little weird....

---

### Post by jirim on 2011-04-21
If you want to use wget through a shell script, you can use following bash script:

```

#!/bin/bash

THREADS=$1
INFILE=$2
PREFIX=filedl

############
#LOGIN DATA#
############
# Note: instead of @ sign use combination %40
EMAIL=user%40gmail.com
PASSWORD=password

COOKIE="/tmp/filesonic.cookie.${RAND}"

# Get cookie with phpsession
wget --save-cookies $COOKIE --keep-session-cookies --post-data="email=${EMAIL}&redirect=%2F&password=${PASSWORD}" http://www.filesonic.com/user/login

PER_FILE=$(( `cat $INFILE | wc -l` / $THREADS ))
rm $PREFIX*
split -d -l $PER_FILE $INFILE $PREFIX
for I in $PREFIX* ; do
    wget -c --load-cookies $COOKIE -i $I &
done
wait
rm $PREFIX*
```Usage:

[LIST=1]
[*]Put your links into a file, each link on a new line a store the file
[*]Run the script:
[/LIST]
```

$ filesonic <threads> <filename>
```Where <threads> parameter is number of parallel downloading threads and is required. Paramter <filename> is name of the file containing your links and is also required.

---

### Post by jirim on 2011-04-22
A little improved code:

```

#!/bin/bash

THREADS=$1
INFILE=$2
PREFIX=filedl

############
#LOGIN DATA#
############
# Note: instead of @ sign use combination %40
EMAIL=user%40gmail.com
PASSWORD=password

COOKIE="/tmp/filesonic.cookie.${RAND}"

# Get cookie with phpsession
wget --save-cookies $COOKIE --keep-session-cookies --post-data="email=${EMAIL} redirect=%2F&password=${PASSWORD}" http://www.filesonic.com/user/login -O - > /dev/null

PER_FILE=$(( `cat $INFILE | wc -l` / $THREADS ))
rm $PREFIX*
split -d -l $PER_FILE $INFILE $PREFIX
for I in $PREFIX* ; do
    wget -c --load-cookies $COOKIE -i $I &
done
wait
rm $PREFIX*
rm $COOKIE

```

---

### Post by Vfool on 2011-08-29
hi, it is possible to download password protected files too?

---

### Post by rrwood on 2011-08-29
Sure-- you just have to supply the password when you unpack them after downloading, right?

---

### Post by ebudmada on 2011-09-11
I guess he is talking about files protected with filesonic webpage password, like [http://www.filesonic.com/file/1781664141](http://www.filesonic.com/file/1781664141)

(had the same problem)

Thanks for the script its awesome!

---

### Post by rrwood on 2011-09-11
So, does the script work for those files?  It is just a matter of supplying a password when you unpack the .rar, right?

---

### Post by ebudmada on 2011-09-11
no, the script does not work for filesonic password protected file (note talking about rar password protection here)

[http://helpdesk.filesonic.com/entries/412554-how-secure-is-filesonic-for-hosting-sensitive-or-confidential-files](http://helpdesk.filesonic.com/entries/412554-how-secure-is-filesonic-for-hosting-sensitive-or-confidential-files)

When you click on "edit" for a file in filesonic, you can rename them, set a description and a password.

I'm not that good in scripting but I guess you have what you need there if you want to add that option: [http://api.filesonic.com/link](http://api.filesonic.com/link)

Thanks again for the script!

---

### Post by ebudmada on 2011-09-11
wget is better because can start multiple threat

anyway i dont know why, can't get it work anymore

python is great too, but much slower (single threat)

---

### Post by ebudmada on 2011-09-11
what are the package i need to make wget bash script work?

i reinstalled my vps and the wget script is not working anymore

i tried ubuntu 10.04, debian 6, gentoo 2008. they are very skinny version but i can add package i got 512mb ram

needed to install wget on ubuntu!

Thanks for helping me!

---

### Post by adonis.parsi on 2011-09-11
> **jirim said:**
> A little improved code:

```

#!/bin/bash

THREADS=$1
INFILE=$2
PREFIX=filedl

############
#LOGIN DATA#
############
# Note: instead of @ sign use combination %40
EMAIL=user%40gmail.com
PASSWORD=password

COOKIE="/tmp/filesonic.cookie.${RAND}"

# Get cookie with phpsession
wget --save-cookies $COOKIE --keep-session-cookies --post-data="email=${EMAIL} redirect=%2F&password=${PASSWORD}" http://www.filesonic.com/user/login -O - > /dev/null

PER_FILE=$(( `cat $INFILE | wc -l` / $THREADS ))
rm $PREFIX*
split -d -l $PER_FILE $INFILE $PREFIX
for I in $PREFIX* ; do
    wget -c --load-cookies $COOKIE -i $I &
done
wait
rm $PREFIX*
rm $COOKIE

```

Thanks dude...just wanted to correct a missing & in the wget --save--cookies
"email=${EMAIL}[COLOR="Red"]&[/COLOR]redirect=%2F&password=${PASSWORD}" also not sure why we have this in wget [COLOR="red"]-O - > /dev/null[/COLOR]

---

### Post by Hayko on 2011-12-11
How can i Use this for php ?

---

