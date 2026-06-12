---
title: "Help with AVI conversion script"
date: 2008-05-31
forum: Ubuntu Studio
---

### Post by stu1978 on 2008-05-31
I downloaded a script from here which successfully converted an avi file i had to a dvd iso image.

The script starts with a 2 pass conversion to avi format before converting to mpg.  If my video is already avi format do i need to go through this stage, or can i delete the part of the script that deals with this?

Cheers.

the script is :



#======================================#
#				       #
# Handy Media To DVD Conversion Script #
# This Script Supports All Media Which #
#      Is Accepted By Mencoder!        #
#				       #
#======================================#
#	Netyire   18/12/2006           #
#    Feel Free To Use For Everything   #
#======================================#

# Thanks To:
# The Gentoo Wiki Specifically This Site: [http://gentoo-wiki.com/Index:HOWTO_Create_a_DVD](http://gentoo-wiki.com/Index:HOWTO_Create_a_DVD)
# The Ubuntu Forum People, For All Their Great Help
# YOU FOR BEING KIND ENOUGH TO USE IT

# Okay, to preserve my sanity, let me first say I do not offer support (Don't call me). But
# If you post your problem on the forums, I will see if I can fix the program (if it is its fault)

# Tested On The Following Specs:
# OS: UBUNTU EDGY EFT 6.10
# MENCODER VERSION: 2:0.99+1.0pre8-0ubuntu8
# FFMPEG VERSION: SVN rUNKNOWN (Wow... Very Helpful :D)
# DVDAUTHOR VERSION: 0.6.11
# MKISOFS VERSION: Includes Unofficial JTE and ICONV Patches (What are those?)
# Anyway, I think they are all from the repositories

# Import OS, So That The Program Can Issue Bash Commands
import os

# First Ask For The Filename
filename = raw_input("Filename:")

# Convert The File To An AVI (XVID 2 Pass + MP3 VBR 3)
# Clear The Screen
os.system("clear")
# Display Pretty Graphics So The User Knows Whats Going On
print "====================="
print "Encoding To AVI...   "
print "Current Pass 1/2     "
print "====================="

# Use Mencoder To Transcode The File To An AVI
# "-ovc xvid -xvidencopts pass=1" Sets The Video Codec To XViD And Specifies Pass 1
# "-oac mp3lame -lameopts vbr=3" Okay, This Sets The Audio Codec To MP3 Using The Lame Encoder And
# Also Sets The VBR To 3 (Variable Bitrate, 1=Best But Biggest, 31=Slowest But Smaller & Worst?)
# "-o dev/null" Specifies No Filename As The Command Outputs To A XVID Log File
os.system("mencoder " + filename + " -ovc xvid -xvidencopts pass=1 -oac mp3lame -lameopts vbr=3 -o /dev/null")

# Clear The Screen
os.system("clear")
# Display Pretty Graphics So The User Knows Whats Going On
print "====================="
print "Encoding To AVI...   "
print "Current Pass 2/2     "
print "Takes More Time Than "	# Print The Nice Graphics
print "Pass 1               "
print "====================="

# ================================================================================================#
# 			      OTHER USERS CONTRIBUTION SECTION					  #
# ================================================================================================#
# Subtitles Part Goes Here (Thanks Rejser For Asking For It :D)                                   #
choice = raw_input("Do you want subtitles [Y/N] (Default: N):")
if choice != "Y":
	choice = "N"
if choice == "N":
	subtitlescommand = ""
if choice == "Y":
	subtitles = raw_input("Please enter the subtitle [only .srt support now] file:")
	subtitlesize = raw_input("Enter The Fonts Scale Size [1-9] (Default:3):")
	if subtitlesize == "":
		subtitlesize = "3"
	subtitlescommand = " -sub " + subtitles + " -subfont-text-scale " + subtitlesize
# =============================================================================================== #

# Mostly The Same As The Command Issued On Pass 1, Except Pass 2 Means Pass 2, A Bitrate Is
# Specified For The Video And The Output Is A Real Filename. I Set The Bitrate To 1000 Because
# I Do Not Know The Quality Of The Users' File So 1000 Is Good Enough
os.system("mencoder " + filename + subtitlescommand + " -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 -o avi.avi")

# Tell The User That Conversion To AVI Went Well
os.system("clear")
os.system("clear")
# Ask for input regarding DVD type and Aspect Ratios
print "==============================================================="
print "Conversion To AVI Completed(Transcoding Step 1/2 Is A Success)" 
print "Please Answer The Following Questions Regarding Your Media"
print "If You Do Not Know, Pressing Enter Uses The Defaults"
print "================================================================"
dvdtype = raw_input("Do you want it PAL or NTSC [PAL/NTSC] (Default:NTSC):")

# Set The Type
if dvdtype == "":
	dvdtype = "ntsc-dvd"
if dvdtype == "NTSC":
	dvdtype = "ntsc-dvd"
if dvdtype != "NTSC":
	dvdtype = "pal-dvd"
aspect = raw_input("Do you want to specify an aspect ratio [Y/N] (Default:N):")

# Set The Aspect
if aspect != "Y":
	aspect = "N"
if aspect != "N":
	aspect = raw_input("Do you want it 16:9 or 4:3 [16:9/4:3] (Default:4:3):")
	if aspect == "":
		aspect = "4:3"
	if aspect != "4:3":
		aspect = "16:9"

# Now Clear The Screen And Encode It To A MPG File According To The User's Specifications
os.system("clear")
os.system("clear")

# Print The Nice Graphics
print "=================="
print "Encoding To MPG..."
print "Wait... :D        "
print "=================="
if aspect == "N":
	os.system("ffmpeg -i avi.avi -target " + dvdtype + " mpg.mpg")
if aspect != "N":
	os.system("ffmpeg -i avi.avi -target " + dvdtype + " -aspect " + aspect + " mpg.mpg")

# Display It Is A Success
os.system("clear")
os.system("clear")
print "================================================"
print "Conversion To MPG Complete (Transcoding Success)"
print "================================================"

# This Continues When The User Presses Enter
raw_input("Press Enter To Continue")
# Clear The Screen
os.system("clear")
os.system("clear")

# Create The DVD Structure
os.system("dvdauthor -o DVD/ -t mpg.mpg")
os.system("dvdauthor -o DVD/ -T")

# Make The ISO
os.system("mkisofs -dvd-video -v -o DVD.iso DVD")

# All Done!
os.system("clear")
os.system("clear")
print "========================================="
print "All Operations Complete, DVD ISO Created!"
print "Netyire 18/12/06                       "
print "Feel Free To Distribute And Build Upon   "
print "========================================="

# Ask If User Wants To Delete Temporary Files
delete = raw_input("Do You Want To Delete Temporary Files [Y/N] (Default:Y):")
if delete != "N":
	os.system("rm divx2pass.log")
	os.system("rm avi.avi")
	os.system("rm mpg.mpg")
	os.system("rm -rf DVD")

# Clear And Display Final Messege
os.system("clear")
os.system("clear")
print "================================="
print "If it worked for you, please drop"
print "me an email at: [email]netyire@yahoo.com[/email]"
print "Please :)                        "
print "================================="
print "Right Click The ISO & Click Write To Disc :D"

---

