---
title: "md5sum password generator"
date: 2012-09-24
forum: Tutorials
---

### Post by test666 on 2012-09-24
This script offers the user the possibility of generating "almost good quality passwords", combing a catchy phrase and a number.

The script, md5sum_password_generator.sh, allows the user to generate non trivial, non easily guessable passwords (32 characters) from a user's (preferably) obscure catch word or phrase, obscuring it further by going trough several md5 sucessive iterations (defined by the user, from 1 up to 99999).

Now the user can "remember" this 32 characters password simply by using the catch phrase and the magic number.

Caveat:
Only a small subset of the available characters is used, the md5 checksum output; numbers **0** up to **9** and small cased letters from **a** up to **f**.

The script: copy/paste into your favorite text editor, save it as md5sum_password_generator.sh (or whatever) and make it executable.
```

#!/bin/bash
# md5sum password generator
# some obscure phrase + an undisclosed number of successive md5sums gives a poor man's two factor authentication ;-)
# yeah, of course this is no two factor authentication, but it was OK and fun building this poorly written script
# if you are going to use this script, remember to clear bash history (my way: wipe -i -P 10 -q -Q 10 -S r -cf ~/.bash_history; history -c)
# or see http://www.reddit.com/r/linux/comments/zqwq8/so_i_just_learned_by_accident_that_commands/
# 2012-September-25, by test666

#BSD license, modified

#Copyright (c) 2012, test666
# All rights reserved.

#Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
#Redistributions of source code must retain the above copyright notice, this list of conditions, the General Notes, The Disclaimer, the Personal notes, the Political note and the following disclaimer.
#Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
#Neither the name of the <ORGANIZATION> nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

#THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

# General notes
# 1 - No time for it now

# Political note
# 1 - unity REALLY, REALLY, REALLY sucks, OMG Ubuntu/Canonical, where are you heading and will I follow you?
# 1.1 - I'm using Lubuntu now, LXDE is OK, humble and super productive
# 2 - #1 NOT flame bait, just venting, cool it, keep it to yourself, no issue here, move along

error ()
{
   echo
   echo "*********************************"
   if [ $# -eq 1 ]
      then
         echo "$1"
         echo "---------------------------------"         
   fi
   echo "syntax : "
   echo "[path]/script.name "'"parameter_1"'" parameter_2"
   echo "./script.name "'"parameter_1"'" parameter_2"
   echo "---------------------------------"
   echo "script.name"
   echo "     md5sum_password_generator.sh"
   echo "---------------------------------"
   echo "parameter_1 : the main password as a"
   echo "      singleword"
   echo "      "'"phrase within quotes"'""
   echo "      phrase«without=spaces_so,no.white<space&allowed"
   echo "---------------------------------"
   echo "parameter_2"
   echo "      number of successive md5 iterations"
   echo "      between 1 and 99999 (or make it bigger and sudo yourself some java)"
   echo "*********************************"
   echo
   exit
}

md5_iterations ()
{
   for (( i  = 1; i <= $iterations ; i++ ))
      do
         catchy_phrase=$(echo $catchy_phrase | md5sum)
         catchy_phrase=${catchy_phrase:0:32}
      done
   echo "$catchy_phrase"
   exit
}

#main
if [ $# -eq 2 ]
	then
	   catchy_phrase=$1
	   iterations=$2
	   max_iter=99999
		case $iterations in
		   [0])
		      error ">>> ERROR: ZERO is not allowed"
			;;
         *[!0-9]*|"")
		      error ">>> ERROR: No number in the second parameter"
			;;
			*)
			   if (( 0 < $iterations && $iterations <= $max_iter )) 
			      then
			         md5_iterations
			      else
			         error ">>> ERROR: NON allowed number"
			   fi
		esac
   else error ">>> ERROR"
fi

```

---

