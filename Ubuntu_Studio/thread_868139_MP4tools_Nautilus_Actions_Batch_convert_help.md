---
title: "MP4tools Nautilus Actions Batch convert help?"
date: 2008-07-23
forum: Ubuntu Studio
---

### Post by BilliShere on 2008-07-23
Ubuntu Hardy 8.04

Well the closest thread I have to this is [http://www.uluga.ubuntuforums.org/showthread.php?p=4560869](http://www.uluga.ubuntuforums.org/showthread.php?p=4560869)

But that is for aac i believe and its a nautilus script. 
What i need here is a nautilus action for mp4tools to batch convert a bunch of random videos in random formats to mp4 for my s60 cell phone.
what i got currently set up in nautilus actions is "convert to mp4". clicking the edit button. under action i have this setup:
path: mks60
parameters: %M
then under conditions tab:
filenames:*.avi ; *.mpg ; *.wmv ; *.mpeg ; *.rm ; *.rmvb ; *.divx
checkmark under appears if selection has multiple files and folder

now the problem is this..This only works if i select one file in nautilus, right click it and press convert to mp4. 

but if i select a couple of files of different or same format and click convert it doesn't happen. I believe this is either a limitation of mp4tools or the command i have set up here under nautilus actions. 

Some help anybody? What am i doing wrong here? or how is the command here wrong?

Even if you got a Nautilus script rather than an action that i can use to batch convert it would be ok. I don't completely understand how to make batch scripts all that well. sorta erm.. noobish at that. I do prefer the more clean Nautilus actions though. lol.

---

### Post by BilliShere on 2008-07-23
what 19 views and no suggestions? no help?
i even tried mks60 %d%f ... doesnt work

---

### Post by aeiah on 2008-07-25
edit: ignore this post

---

### Post by aeiah on 2008-07-25
nevermind i see what mks60 is now. so, how do you use mks60? can you use it as is for multiple input files?

you need a script that will iterate through your input files because right now when you select more than 1 file and use your nautilus-actions thing it basically sends this command 
```
mks60 'path/to/file/1.avi', 'path/to/file/2.mpg', 'path/to/third/video.avi'

```

which is probably gonna confuse mks60

---

### Post by aeiah on 2008-07-25
try creating a bash script that does this:
```

#!/bin/bash
for f ; do
mks60 $f
done

```

and launching that from nautilus actions

---

### Post by BilliShere on 2008-07-25
ok im trying that out right now... will report on how it worked.

as far as i know...i dont think i can use mks60 to do that multiple file thing.. and you are right about it confusing mks60

---

### Post by BilliShere on 2008-07-25
ok the bash script didn't work at all..im gonna try it as a nautilus script now. that didn't work either.. 

i found an alternative though.. wonder why it didn't turn up before on google when i was searching?

Its called mp4size.. just install it under nautilus scripts

Here it is... 


#!/usr/bin/ruby -w
#
# Copyright (C) 2007 Thomer M. Gil [[http://thomer.com/]](http://thomer.com/])
# Thanks to Brian Moore for bugfixes.
#
# This program is free software. You may distribute it under the terms of
# the GNU General Public License as published by the Free Software
# Foundation, version 2.
# 
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General
# Public License for more details.
# 
# This program converts video files to mp4, suitable to be played on an iPod.
# It is careful about maintaining the proper aspect ratio.
#

require 'getoptlong'

DEFAULT_ARGS = "-f mp4 -vcodec xvid -maxrate 1000 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac"
DEFAULT_AUDIO_BITRATE = 128
DEFAULT_VIDEO_BITRATE = 400
WIDTH = 320.0
HEIGHT = 240.0

$options = {}
opts = GetoptLong.new(
  [ "-a", GetoptLong::REQUIRED_ARGUMENT ],      # audio bitrate
  [ "-h", GetoptLong::NO_ARGUMENT ],            # help
  [ "-b", GetoptLong::REQUIRED_ARGUMENT ],      # video bitrate
  [ "-v", GetoptLong::NO_ARGUMENT ]             # verbose
)
opts.each { |opt, arg| $options[opt] = arg }

if $options['-h']
  puts <<EOF
mp4ize - encode videos to mp4 for an iPod

Usage: mp4ize file1.avi [file2.mpg [file3.asf [...]]]


Options:

  -h       : this help
  -v       : verbose
  -a RATE  : override default audio bitrate (#{DEFAULT_AUDIO_BITRATE})
  -b RATE  : override default video bitrate (#{DEFAULT_VIDEO_BITRATE})
EOF
  exit
end

audio_bitrate = $options['-a'] || DEFAULT_AUDIO_BITRATE
video_bitrate = $options['-b'] || DEFAULT_VIDEO_BITRATE

ARGV.each do |infile|
  outfile = infile.dup
  ext = File.extname(outfile)
  outfile.sub!(/#{ext}$/, '.mp4')

  # open the file to figure out the aspect ratio
  w, h = nil, nil
  IO.popen("ffmpeg -i '#{infile}' 2>&1") do |pipe|
    pipe.each_line do |line|
      puts line
      if line.match(/Video:.+ (\d+)x(\d+)/)
        w, h = $1.to_f, $2.to_f
      end
    end
  end

  begin
    aspect = w/h
  rescue
    puts "Couldn't figure out aspect ratio."
    exit
  end

  height = (WIDTH / aspect.to_f).to_i
  height -= 1 if height % 2 == 1
  pad = ((HEIGHT - height.to_f) / 2.0).to_i
  pad -= 1 if pad % 2 == 1

  File.unlink(outfile) if File.exists?(outfile)
  cmd = "ffmpeg #{DEFAULT_ARGS} -i '#{infile}' -s #{WIDTH.to_i}x#{height} -padtop #{pad} -padbottom #{pad} -ab #{audio_bitrate} -b #{video_bitrate} '#{outfile}'"
  puts cmd if $options['-v']
  system cmd
end

---

### Post by BilliShere on 2008-07-25
Thanks for the help though!

---

### Post by Sanketsu on 2008-08-14
I'm looking for something very similar, but for the mkpsp part of mp4tools.

Anyone have any suggestions?

---

