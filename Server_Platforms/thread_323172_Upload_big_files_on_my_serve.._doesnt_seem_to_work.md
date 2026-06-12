---
title: "Upload big files on my serve.. doesnt seem to work"
date: 2006-12-21
forum: Server Platforms
---

### Post by envis on 2006-12-21
Hi, i seem to have a little problem when ppl try to upload files on my server...

many ppl have uploaded files on my server already without a poblem... but one of my friends was trying to upload a 100Mb Dj Mix on my website and it always just times out...

i use the PHP upload method to upload on my server....
uploads for smaller files work withouth a problem...

i have already set the max upload file size to 200Mb in my php.ini...

but i thoughed maybe something in my apache could need to be changed to not time out or something like that.....

does anyone have any idea what i should be set to make sure a 100Mb upload to my server can go through?

---

### Post by MJN on 2006-12-22
This coule be a read herring however I had issues with my Squirrelmail (webmail) installation when trying to upload 'large' attachments.
 
The fix was to edit php.ini as you have done, however I needed to increase **memory_limit** and **post_max_size** in addition to **upload_max_filesize**.
 
Again, it might be of no use but anything's worth a shot...
 
Mathew
 
P.S. According to my poorly written notes from that era I also made the **limitrequestbody** directive unlimited (set it to zero) in /etc/apache2/mods-available/php5.conf however I'm not entirely sure this was to fix this particular issue hence could be even more of a red herring.

---

### Post by envis on 2006-12-22
ok, thanks MJN. i did the changes you suggested in my php.ini + a few other things i could find, like time out limits in apache as well... though i didnt have a limitrequestbody directive in /etc/apache2/mods-available/php5.conf (theres just 2 lines of stuff in that file for me)..

i will be testing that tongiht...

but i have another little question....

about the uploads user can do on my website again:

ppl are supposed to upload mp3 files on my server and again, for most ppl it seems to work fine.

the PHP script that handles the upload is verifying the mime type of the uploaded file and makes sure it is audio/mpeg. otherwise it says, sorry thats not a mp3... and me on my computers and all computers ive tried with all mp3 ive tried, all this has always been working fine...

but some ppl sometimes apparently are really trying to upload mp3 and the system recognizes it as other things... 

like lately, one guy was trying to upload his songs but his songs were seen as text/html!!!

yet, this guy swears that he has been making mp3 audio since 2001 and never had a problem uploading his songs anywhere else.....

why is my system recognizing his song as text/html then?

just for safety, i went ahead and started accepting also audio/x-mpeg, audio/mpeg3, audio/x-mpeg3, audio/x-mpg, application/force-download, application/mp3, audio/x-mpegaudio and application/x-mp3... but that really has changed nothing...

do you think maybe my system might be lacking some mp3 libraries to recognize all types of mp3 successfuly?

what libraries would i need?

or is there any other possible reason for that except the possiblity that the perticular user's computer is good for garbage or that his mp3 encoder is crap...

keep n mind that this user says that all other websites have been accepting his mp3 without a problem... and he's not the first user haroving a similar pblem and saying that it works everywhere else..!

i must admit that i work as internet tech support and the "but it works everywhere else"  is a classic for the client to make you feel that its your fault lol... but i still assume that its true and therefore there must be something wrong with my server... or my scripts...

?

---

### Post by MJN on 2006-12-22
How are you working out the MIME type for the uploaded file? By file extension? If so, could it be getting tricked by any other dots in the filename? (I would hope not)

Or, is it getting the MIME type from the client's browser? In which case, perhaps this person's browser is not sending the MIME type correctly, or at all.

Indeed, if some files are being recognised at text/html then I'd suspect a client browser issue.

Mathew

---

### Post by envis on 2006-12-23
no, i think i really check for the mime type not jsut the extension, the part of my script that verifies the mime type looks like:

if($_FILES['uploadedfile']['type'])=="audio/mpeg")
{
//go ahead and upload...
}

but i thoughted that the mime type was verified by my server, not the browser...
thats why i went ahead and installed more mp3 related librairies on my server...
but if its the browser then... maybe i should just ask the user to try with another browser.... (if he still wants, he's a bit pissed cos i suggested that maybe his mp3 was not properly encoded :P)

anyways thanks for the info

---

### Post by envis on 2006-12-23
what if, i first uploaded any file submitted to me in a quarantine folder without checking the mime type at all, and then, made PHP verify the mime type on the file in the "quarantine" folder?

would the file still have the erroneous mime type that the browser was giving it, or would my system re-evaluate the mime type itself?

---

### Post by MJN on 2006-12-23
I'm afraid I don't know PHP well enough to advise you on those specifics...
 
However I do know it's only likely to be guessing the MIME type by either the file extension or by utlising the system's file command. Or of course the client browser header but I can't tell from the context of your script which it is.
 
What I do know however is that it's highly unlikely to be the guy's MP3 - an MP3 is an MP3...
 
Mathew

---

### Post by envis on 2007-01-04
i still cant upload the a 100M file on my server, it times out

my upload_max_filesize is already at 2000M in php.ini

as MJN suggested, i set post_max_size to 2000M as well though i was affraid to set the memory_limit to 2000M cos it says "Maximum amount of memory a script may consume (8MB)" next to it...

actually im looking at this part here:
max_execution_time = 30     ; Maximum execution time of each script, in seconds
max_input_time = 60 ; Maximum amount of time each script may spend parsing request data
memory_limit = 8M      ; Maximum amount of memory a script may consume (8MB)

max_execution_time = 30? it will prolly take more than 30 seconds to upload a 100M file, should i change that?

MJN also suggested that i set limitrequestbody directive unlimited (set it to zero) in /etc/apache2/mods-available/php5.conf

but that thing does not seem to be in this file, it only contains
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
in my case....

there must be a way to make a 100M upload work... please help!:confused:

---

### Post by MJN on 2007-01-05
Ignore the limitrequestbody directive I mentioned - if you don't have it explicitly defined then it defaults to unlimited.

Just whack all your suspect settings right up and see if it works. The '8MB' comment is merely explaining what the default setting is.

What's your server's download speed (and your mate's upload speed)? My upload is limited to only 384kbps so I'd need at least 2048 seconds allowance for the 100MB upload to take place (if not somewhat more given the transfer overheads and other delays).

Mathew

---

### Post by envis on 2007-01-06
ok.. ok... im gonna boost that value.. i was scared of boosting it cos it sounds to me like how much RAM can a script consume... 

so i was thinking.. a long upload is not gonna take that much RAM... but an accidental infinite loop or something like that could crash the server if i allow it 2000M of RAM...

but im running some tests on this right now...

by the way, its pretty interesting all you can do with apache.. once you know how..

(like customized error pages for example...)

i'll post my resluts...

---

### Post by envis on 2007-01-06
allright!!! its working now...

i did boost my memory_limit to 2000M

and set all the "time-outs" that seemed to be related in /etc/apache2/apache2.conf and /etc/php5/apache2/php.ini to 900 to allow 15 minutes

it is very educative to read those 2 files actually!

restarted apache and when i tried uploading the 100M file again, it went through after a few minutes and gave me a big "upload succesful" message :D 

thanks a lot for your help MJN!!!!

---

### Post by MJN on 2007-01-06
Good to hear it!

Now remember to wind the figures back down to something sensible - no point in giving too much overhead as, as you say, the limits are there for a reason and hence making them sky high could come back to bite you.

Mathew

---

