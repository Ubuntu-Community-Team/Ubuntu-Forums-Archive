---
title: "[Ann] logprofIM - improves logprof by managing syslog marks"
date: 2007-12-09
forum: Server Platforms
---

### Post by Adnarim on 2007-12-09
Hi,
I wrote a little script in ruby which extends AppArmors logprof with the ability to set and remind marks in the logfile. This is a feature I really missed and is quite usefull if you use logprof to check for unallowed actions which have been tried or you simply want to update the profile of an app.

If you can german you will find here an article about it: [http://wiki.ubuntuusers.de/Skripte%20logprofIM](http://wiki.ubuntuusers.de/Skripte%20logprofIM)

Here's the code:
```

#!/usr/bin/env ruby
#
#	logprofImProved 0.1
#
#	by Adna rim
#
# for more information execute: logprofIM -h

$VERBOSE=true

$Version="0.1"
Path_to_config = ENV['HOME']+'/.logprofIM'

class LogprofIM
	
	def initialize
		system("mkdir #{Path_to_config}") if not FileTest.exists?(Path_to_config)
		system("touch #{Path_to_config}/mind") if not FileTest.exists?(Path_to_config+'/mind')
		$minded_marks=[]
		File.open(Path_to_config+'/mind').each { |line| $minded_marks<<line if not line.match(/^\s+$/) }
	end
	
	def parse_cmdl
		$use_ui=true
		@no_mark=false
		@ask=false
		
		printversion if $*.include?("--version")
		printhelp if $*.include?("-h")
		
		if $*.include?("-o") &  $*.include?("-n")
			puts "Wrong parameters. -o and -n can't be used together.\nSee the help (-h) for more information."
			exit
		elsif $*.include?("-o") &  $*.include?("-u")
			puts "Wrong parameters. -o and -u can't be used together.\nSee the help (-h) for more information."
			exit
		elsif $*.include?("-u") &  $*.include?("-n")
			puts "Wrong parameters. -u and -n can't be used together.\nSee the help (-h) for more information."
			exit
		end
		
		@no_mark = true if $*.include?("-nm")
		@ask = true if $*.include?("-a")
		if $minded_marks.size == 0
			@mark_to_use=''
		elsif $*.include?("-o")
			@mark_to_use = $minded_marks[0]
			$use_ui=false
		elsif $*.include?("-n")	
			@mark_to_use = $minded_marks[$minded_marks.length-1]
			$use_ui=false
		elsif $*.include?("-u")	
			@mark_to_use = ''
			$use_ui=false	
		end
	end

	def ui
		puts "Which mark should be used:"
		printf " o)ldest\n n)ewest\n u)se no mark\n\n"
		0.upto($minded_marks.length-1)  { |i| puts " #{i}.) #{$minded_marks[i]}"}
		print "Input: "
		input1 = STDIN.readline
		case input1.chomp
			when 'o':@mark_to_use = $minded_marks[0]
			when 'n':@mark_to_use = $minded_marks[$minded_marks.length-1]
			when 'u':@mark_to_use = ''
			else 
				if input1.chomp.match(/\d/)
					@mark_to_use = $minded_marks[input1.chomp.to_i]
				else exit
				end
		end
	end

	def execlogprof
		@mark_to_use='"'+@mark_to_use.chomp+'"'
		@logprof_status = system("sudo logprof -m #{@mark_to_use}")	
	end
	
	def savemark
		if @logprof_status == true and @no_mark==false
			@mark="MARK#{Time.now.strftime("%d%m%Y%H%M%S")}"
			system("echo #{@mark} >> #{Path_to_config}/mind") if system("sudo su -c 'echo #{@mark} >> /var/log/messages'")	
		end	
	end

	def createnewmark
		if @ask == true
			puts "\nShall I place a mark?(y/n)"	
			print "Input: "
			if STDIN.readline.chomp=='y'
			@no_mark=false	
			savemark 
			end	
		else 
			savemark	
		end
	end
	
	def printversion
		puts "logprofIM version #{$Version}\n    by Adna rim"
		exit
	end
	
	def printhelp
		puts "NAME"
		puts "			logprofIM"
		puts "SYNOPSIS"
		puts "	logprofIM [-o] [-n] [-u] [-a] [-nm] [-h] [--version]	"
		puts ""
		puts "DESCRIPTION"
		puts "	logprofIM improves logprof with the ability to set\n	and remind about logmarks."
		puts ""
		puts "OPTIONS"
		puts "	-o	starts logprof with the oldest mark"
		puts "	-n	starts logprof with the newest mark"
		puts "	-u	starts logprof with no mark"
		puts "	-h	prints this help"
		puts ""
		puts "	--version	prints the version information"
		puts ""
		puts "	NOTE: If none of the above commandline options are given the inter-\n	      active userinterface will be started."
		puts""
		puts"	-a	ask before saving a mark in the logfile"
		puts"	-nm	don't save a mark in the logfile"
		puts""
		puts "	NOTE: -a and -nm affect both, the acting of logprofIM in\n	      commandline-mode and in the interactive userinterface."
		exit
	end
	
end

mylogim = LogprofIM.new
mylogim.parse_cmdl
mylogim.ui if $use_ui==true  and $minded_marks.size != 0
mylogim.execlogprof
mylogim.createnewmark

```

Any feedback is welcome :)

greets

---

