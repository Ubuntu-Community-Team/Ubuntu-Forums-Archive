---
title: "nested if else 'unexpected &quot;;&quot; ? please help."
date: 2012-05-12
forum: Server Platforms
---

### Post by alexinoz on 2012-05-12
Hi all,

My first post. I have been reading this forum for a fair while though. And a lot of other recently. Up until now I have solved all the problems I have had by reading what is out there. This one I can't.

I am writing a back up script. I read the users from a text file and then run a loop to iterate the back up procedure for each user.

I have just now added a nested if else and I am getting an error at the first line listed below,

		if [[ -f /var/log/snar/${i}5.snar]]; then

			mv /var/log/snar /var/log/snar/backup
			rm -rf /var/log/snar

It is telling me there is an unexpected semi colon.

I believe it may be something inside the condition brackets but I don't know.

Here is the complete script (not finished but as it is now).

```
#!/bin/bash


            #############################################
            # 	                                        #	    	
	    # Backup to /media/external NTFS USB device #	    
	    #						#	    	
	    #############################################



# Populate User list array from text file

	# Set field separator value to new line

		old_IFS=$IFS
		IFS=$'\n:'

	# Create array

		users=($(cat ./userlist.txt))
			
	# Reset IFS to default

		IFS=$old_IFS
	
	# Print Contents of Array
		echo
		echo
		echo "Initialising"
		echo "Please Wait"
		echo 
		echo 
		echo "Users to be backed up: ${users[*]}"
		echo 
		echo 
		echo "You can add users to the backup list \
			 by editing userlist.txt"

	# Mount directory for backup
			 
	sudo mount -t ntfs-3g /dev/sdb1 /media/external
		
		echo 
		echo 	

	# Assign users for backup

		################
		## START LOOP ##
		################

		for i in  ${users[@]}; do
			
	# Back up source 
	
		BACKUP_SOURCE="/home/${i}"

		echo 
		echo 
		echo " BACKUP SOURCE IS ---------- $BACKUP_SOURCE"

	# Back up destination

		DEST="/media/external"
	
	# Create archive filename

		ARCHIVE_FILE="${i}-$(date +%Y%m%d).tar.gz"
		date
		echo

	# Print start status message.

		echo "Backing up $BACKUP_SOURCE to $DEST/$ARCHIVE_FILE"
		date
		echo
		echo 
		echo 

	# Backup the files using tar [And create snapshot file for incremental]

		if [[ -f /var/log/snar/${i}5.snar]]; then

			mv /var/log/snar /var/log/snar/backup
			rm -rf /var/log/snar

		else if [[ -f /var/log/snar/${i}4.snar]]; then
				tar -cvW \
				= $DEST/$ARCHIVE_FILE $BACKUP_SOURCE \
				--listed-incremental=/var/log/snar/${i}5.snar


		else if [[ -f /var/log/snar/${i}3.snar]]; then

			tar -cvW \ 
			= $DEST/$ARCHIVE_FILE $BACKUP_SOURCE \
			--listed-incremental=/var/log/snar/${i}4.snar

		else if [[ -f /var/log/snar/${i}2.snar]]; then

			tar -cvW \ 
			= $DEST/$ARCHIVE_FILE $BACKUP_SOURCE \
			--listed-incremental=/var/log/snar/${i}3.snar

		else 		
			tar -cvW \ 
			= $DEST/$ARCHIVE_FILE $BACKUP_SOURCE \
			--listed-incremental=/var/log/snar/${i}.snar
		
		fi

	fi

	# Print end status message.

		echo
		echo "Backup of ${i} Complete"
		date
		echo 
		echo 
	
	# End Loop

		done

	# Long listing of files in $dest to check files sizes.

		echo "The following is a list of files in your backup directory..."
		ls -lh $DEST
		echo
		echo
		echo 
		echo 
		echo "Today's Backup is Complete"
		echo 
		echo 	
		echo "Please wait while External Media is removed"
		echo
		echo 
	
	# Unmount external drive

	echo "Removing external drive from mount..."
	sudo umount /media/external
```

---

### Post by CharlesA on 2012-05-12
Change:
```
mv /var/log/snar /var/log/snar/backup
rm -rf /var/log/snar
```

to:

```
mv /var/log/snar /var/log/snar/backup && rm -rf /var/log/snar
```

Makes it neater. Did the error tell you a line number?

---

### Post by alexinoz on 2012-05-12
Line number is 83.

# Backup the files using tar [And create snapshot file for incremental]

		if [[ -f /var/log/snar/${i}5.snar]]; then

---

### Post by CharlesA on 2012-05-12
Try commenting everything inside the if then statement out and see if it gives you the same error.

---

### Post by alexinoz on 2012-05-12
I commented it out. The error disappears.

The if else is new. I had the script running fine as a full back up but I have added in the nested if else to incorporate incrementals.

---

### Post by papibe on 2012-05-12
Hi alexinoz.

There are syntax errors on your script.

Here's a couple that I can see easily:

1. There should be no space between the if's expression and the bracket. Change this:
```
if [[ -f /var/log/snar/${i}5.snar]]; then
```
for this:
```
if [[ -f /var/log/snar/${i}5.snar ]]; then
```
Although in this case you don't need double parenthesis, so this should work:
```
if [ -f /var/log/snar/${i}5.snar ]; then
```

2. The correct else-if is like this:
```
if
    ...
elif
    ...
elif
    ...
else
   ...
fi
```

Hope that helps.
Regards.

---

### Post by CharlesA on 2012-05-12
I've always added a space when using: [[ ... ]]

I'm guessing using elif will fix the problem.

---

### Post by alexinoz on 2012-05-12
Hi CharlesA, papibe,

the elif fixes the problem. I have other syntax errors but I will try fix them myself before I ask again.

Thank you.

---

### Post by alexinoz on 2012-05-12
I have attached an image, cut out from screenshot of errors as I am running vm Ubuntu server so its difficult to log usb in and out timely.

Receiving syntax errors, missing " ' " on each line when elif begins.

also, 

tar: tar: cannot verify stdin/stdout archive.
underneath the tar error is,

line 108=: command not found, 108 is operation for else condition. 

else
  tar -cvW \
---> $DEST/$ARCHIVE_FILE $BACKUP_SOURCE \

---

### Post by alexinoz on 2012-05-12
sorry, just to explain that a bit more:

The backup destination is empty so none of the previous conditions would be met,

Clearly,

I have something wrong with the statement (which is repeated in ease case with an extension to the file name.

previously I had different options on the tar command.

Is there anything obviously wrong with my tar command or the incremental option?

---

### Post by alexinoz on 2012-05-12
Almost resolved.

incremental command didn't belong in final condition. That's is the full back up.

Still can't work out why or where I am supposed to be quoting around the elif. Anyone?

---

### Post by papibe on 2012-05-12
Could you post the new corrected version? I would be easier to take a look ;)

Regards.

---

### Post by alexinoz on 2012-05-12
Thanks for replying back.

I worked it out... After a little bit of swearing and the sun coming up :)

then lines were almost identical, 

elif [ -f /var/log/snar/${i}3.snar]
elif [ -f /var/log/snar/${i}4.snar] etc

the issue was the lack of a space next to the closing bracket.

Pretty damn happy now. Not yet finished but got that part sorted out.

Thanks again.

---

