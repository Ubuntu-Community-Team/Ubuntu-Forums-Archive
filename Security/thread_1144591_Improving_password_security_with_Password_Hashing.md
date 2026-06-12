---
title: "Improving password security with Password Hashing"
date: 2009-04-30
forum: Security
---

### Post by nobodysbusiness on 2009-04-30
I recently discovered "Password Hashing", and decided to implement it with all of my online accounts (including Ubuntu Forums, of course). It was a bit rocky to get started, so I decided to write [this blog post]("http://pragmattica.wordpress.com/2009/04/30/password-hashing-a-neat-idea-that-can-help-to-protect-your-online-accounts/") in the hopes of helping others. Let me know what you think.

---

### Post by HermanAB on 2009-05-01
Uhmmm... your password is still sent in plain text over the internet to Ubuntu Forums.

Decent mail and banking solutions use HTTPS, so in that case your credentials are encrypted end to end already.

So it seems to me that you haven't actually achieved anything useful security wise.

---

### Post by disabledaccount01 on 2009-05-01
Message removed by author.

---

### Post by kevdog on 2009-05-01
This is not a new concept -- just one newly discussed in the Ubuntu Forums.  Putting the theory aside, I wonder if this actually improves security, or is just another method of providing security through obscurity.  The author states that methods such as using KeyPass to store passwords and is inconvenient, however I fail to see how the proposed method doesn't levy a similar type of inconvenience.  I thanks the author for his contribution.  It makes for an interesting discussion, however the universal practicality of the solution proposed is questionable as well as the real security advantages.

---

### Post by nobodysbusiness on 2009-05-01
@HermanAB: Password Hashing is all about damage control. You can go on using one password for all your sites, enjoying the same convenience that a non-security-conscious person would get. However, if one password is compromised, that's only one account that you've lost. Someone could steal my Ubuntu forums account and post nasty messages, but they couldn't log in to my bank and take my money.

@Enos: You bring up an interesting point about key loggers. I read about those for a while, and there's really only one method that I know of that could really help with a key-logging situation. I read about a security-oriented web-site that would generate one-time passwords and display them to you at home, so that when you're on the road, at an internet cafe, you could log in to their site with a one-time password instead of your regular password. The one-time password would only allow you to log in once, so it would be useless to anyone who stole it with a keylogger. Do you know of any other solutions?

@kevdog: I don't think that password hashing qualifies as security through obscurity, because you can tell everyone in the world exactly how you're protecting your web accounts, including the exact hashing algorithm that you're software uses (and even the software source-code). As long as your master password is kept safe, you don't have to worry. You're still secure.

---

### Post by Dr Small on 2009-05-01
> This online version shouldn’t need to transmit anything over the Internet in order to generate the password for any of your websites.
That statement is not correct (of course, depending on the software that you rely on to hash the password.) PwdHash.com requires user input from the browser to the server. Thankfully, pwdhash.com uses HTTPS encryption to the server.

But, you are sending your plaintext master password to the server. So, always be sure that the server you are connecting to is secure, first.

I actually thought of this method several months back, and wrote a single small password hasher script in Php to take user input, hash it is md5 and then in sha1. My script was more for generating random passwords in a rememberable format. I gave the option to specify a character limit, and then alphabetically sort the characters in the limit to make the new password.

It's a single file, so it's nothing fancy. (Unfortunately, I don't have it up on the web anywhere, since nathangrubb took down my userspace at grubbn.org...)


I actually have been using this concept to generate my new passwords, because if I ever forget the password (unlikely, but still a risk factor) I have a method to rehash it from the phrases that I hash.

```
<?php
/**
 * Project: PassGen
 * Author: Dr Small <drsmall@mycroftserver.homelinux.org>
 * Creation Date: Day 019, 2009
 * Description: Generates Hash passwords based on input.
*/


// Define a few variables for starting.
$length = $_POST[length];
$word = $_POST[word];
$show = $_GET[show];


// Return the default, top part of the page.
echo
'<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
	<head>
		<title>PassGen - Password Generator</title>

		<style type="text/css">
			body { padding: 10px 5% 10px 5%; margin: 0px;}
			table { border: 1px solid #3d3d3d; width: 100%; background-color: #c4c4c4; }
			td { padding: 5px; text-align: left; font-size: xx-large; color: #000000;}
			td.about { padding: 5px; text-align: left; font-size: medium; color: #000000;}
			td.hide { color: #c4c4c4; text-align: center;}
			td.hide:hover { color: #000000; text-align: center;}
			div { text-align: left; font-size: xx-large; }
			input { font-size: x-large; }
			input.hide { color: #FFFFFF; }
			input.hide:hover { color: #000000; }
			select { font-size: x-large; }
		</style>
	</head>
	<body>

		<form action="'.$_SERVER[PHP_SELF].'" method="post">
		<div>
			<br />
			Password Generator:
			<table>
				<tr>
					<td>String: </td><td><input class="hide" type="text" name="word" value="'.$word.'"/></td>
					<tr></tr>
					<td>Length: </td><td><select name="length">'."\n";


			$stoplimit = "41";
			$startlimit = "5";
			$currentlimit = '5';
			// The while loop starts at 5 and ends at 40
			// And since $currentlimit gets increaded by 1 after
			// the text has been echoed, we make the stop limit 1 greater.

			while($currentlimit == $startlimit or $currentlimit > $startlimit && $currentlimit < $stoplimit){
				if($currentlimit == $length){
		echo '		<option value='.$currentlimit.' selected="selected">'.$currentlimit.'</option>'."\n";
				} else {
		echo '		<option value='.$currentlimit.'>'.$currentlimit.'</option>'."\n";
				}
				$currentlimit++;
			}
		echo '
					</select></td>
					<tr></tr>
					<td></td><td><input type="submit" value="Generate" /></td><td style="text-align: right; font-size: large;">[<a href="'.$_SERVER[PHP_SELF].'?show=about">ABOUT</a>]</td>
				</tr>
			</table>
		</div>
		</form>';

// If length of the string has been specified, proceed.
if($length){

	// Hash the input string.
	$md5hash = md5($word);
	$shahash = sha1($md5hash);


	// PHP4 COMPATIBILITY!!
	if(! function_exists('str_split')){
		function str_split($text, $split = 1){
			$array = array();
			for ($i = 0; $i < strlen($text);){
				$array[] = substr($text, $i, $split);
				$i += $split;
			}
			return $array;
		}
	}


	// Split it up into single characters.
	$chars = str_split($shahash, 1);

	// Sort them numerically.
	sort($chars, SORT_NUMERIC);

echo '

		<div>
			<br /><br /><br />
			MD5 Hash:<br />
			<table>
				<tr>
					<td class="hide">'.$md5hash.'</td>
				</tr>
			</table>

			SHA1 Hash:<br />
			<table>
				<tr>
					<td class="hide">'.$shahash.'</td>
				</tr>
			</table>

			<br /><br />

			New Password:<br />
			<table>
				<tr>
					<td class="hide">';

			// Return each character from the $chars
			// array on the page.
			$limit = '0';
			foreach($chars as $char){
				if($limit < $length){
					echo $char;
					$limit++;
				}
			}

		echo '</td>
				</tr>
			</table>
		</div>
	</body>
</html>';


	// Take the contents of the wastecan and dump them in the fire. :)
	// First, we set each variable to a specific value to overwrite
	// the previous contents, then we unset the variables for extra
	// security. I don't take any chances.
	$word    = '001011110000001000000001';
	$length  = '001000010000001000000001';
	$md5hash = '001011110000001000000001';
	$shahash = '001011110000001000000001';
	unset($word, $length, $md5hash, $shahash);

	foreach($chars as $key => $char){
		$chars[$key] = '0001000010000001000000001';
		unset($chars[$key]);
	}


// Define a seperate page.
} elseif($show == "about"){
	echo '
		<div>
			<br /><br /><br />
			About<br />
			<table>
				<tr>
					<td class="about">
						This password generator takes the input from a word, string
						or poem, takes that input and makes a md5 hash out of it. This
						hash is then outputted in the MD5 Sum table. Next, the password
						generator takes the MD5 Sum and runs it through the SHA1 hash
						function to generate a SHA1 hash off of the MD5 Hash.<br />
						<br />
						Next, based upon your selection of password length, the generator
						outputs the first x amount of characters in the New Password table.
						<br /><br />
						At first glance, you will notice that the tables contain no visible
						text. Simply hover your mouse over the table and the hash/password
						will appear. This should keep people from looking over your shoulder
						at the newly created password hashes.<br /><br />
						All string inputs are <em>not</em> recorded, as complete privacy
						is our goal.
					</td>
				</tr>
			</table>
			<br /><br />

			Disclaimer<br />
			<table>
				<tr>
					<td class="about">
						PassGen does not store any of your input strings, password
						lengths, md5 hashes, sha1 hashes or sorted strings (passwords).
						Instead, this program goes to great lengths to wipe all such data
						from cache to verify your privacy.<br />
						<br />
						Passwords are a sensitive thing and should not be taken lightly.
						Generating a long yet rememberable password is essential to your
						security and privacy. The minimum length limit for generating a password
						has been set to 5, as anything below that can most usually be
						guessed/cracked within a short amount of time.<br /><br />
						
						The creators of PassGen can not be held responsible if
						the password you have chose can be or has been cracked. Such
						a guarantee is impossible since technology advances and
						users make mistakes.
					</td>
				</tr>
			</table>
			<br /><br />

			Source<br />
			<table>
				<tr>
					<td class="about">
						PassGen is released under the [<a href="http://creativecommons.org/licenses/GPL/2.0/">GPL License</a>].
						Feel free to use and distrubite this software. 
						You may download the single source file from [<a href="'.$_SERVER[PHP_SELF].'s">here</a>].
					</td>
				</tr>
			</table>
		</div>
	</body>
</html>';

}

?>
```

---

### Post by nobodysbusiness on 2009-05-01
If the PwdHash web version actually does transmit information to a server, then that means that this quote from the PwdHash website is incorrect:

> Javascript computes the password hash on the local machine (so that the user's password is never communicated to Stanford). The resulting hashed password can be pasted into the user's web login form.

The quote can be found [here]("http://crypto.stanford.edu/PwdHash/"). I haven't actually looked at the Javascript code for the web version of PwdHash, so I honestly don't know if they're telling the truth or not. I would imagine that the Firefox extension version of PwdHash definitely wouldn't need to send anything over the Internet. If this software is indeed sending master passwords over the Internet, then perhaps these Stanford people aren't as trustworthy as they seem.

Anyway, that's a neat script. The ability to regenerate hard passwords would be very helpful if you are hoping to try to remember them and never write them down.

---

### Post by Dr Small on 2009-05-01
Yes, the site does use javascript (I missed that before) and javascript is clientside, so no data is being sent to the server. But, so long as whatever password hashing script you are using across the interent is using SSL, then you shouldn't have to worry about having your master password sent in plain text.

Dr Small

---

### Post by disabledaccount01 on 2009-05-01
Message removed by author.

---

### Post by benbenben on 2009-05-02
> **nobodysbusiness said:**
> I read about a security-oriented web-site that would generate one-time passwords and display them to you at home, so that when you're on the road, at an internet cafe, you could log in to their site with a one-time password instead of your regular password. The one-time password would only allow you to log in once, so it would be useless to anyone who stole it with a keylogger. Do you know of any other solutions?


How about [KYPS]("http://kyps.net")?

---

### Post by ooobooontooo on 2009-05-04
Excuse me, if I'm slightly off topic, but I think I read in a book (I think it was Security Engineering by Ross Anderson...excellent book btw) where they conduct an experiment regarding the "difficulty" of passwords. I think it said that an experiment was conducted somewhere and basically strategies such as taking the first letter of a sentence that you will remember proved to be just as effective as a hash. And because memorizing hashes are difficult in most cases, the strategy-method also proved effective memory-wise....just throwing that out there.

The book goes more into it and talk about characterizations of passwords and all that...sorry I sound like a salesman, but it is a good book and I do recommend it.

---

### Post by nobodysbusiness on 2009-05-04
I definitely agree that remembering the first letter of each word in a phrase is a good way to come up with a password (provided that you can work numbers and punctuation in there somehow). But the password hashing question is not so much about generating passwords as it is about using them. If you generate one good password, should you use that one password on all of your websites, or use different passwords for each website? Even if your password is good, it could still get stolen, and then the hacker would have the password for every single website that you use.

---

### Post by nobodysbusiness on 2009-05-04
@benbenben: I've been reading about KYPS, and it seems pretty neat. Unfortunately, it still requires you to trust the KYPS people, as they are able to take the one-time codes and decrypt them to your true password for that website. That means that KYPS is a single point of failure for your web-site security. If only there were some way to do something like this without trusting any specific website any more than you have to for the website to perform its function. As an example, if you use the Dropbox online service to backup your files, and you encrypt the files before sending them over, then you don't have to trust the Dropbox people very much. After all, you're doing the encryption yourself, and Dropbox can't break it any more easily than anyone else. Perhaps every website should have the ability to generate one-time codes as well as allowing a password-based login. Every site in existence supports the use of passwords for security. Maybe one-time codes should be supported as well? (Not that I think this will every happen)

---

### Post by ooobooontooo on 2009-05-04
I apologize for my reply earlier. I obviously didn't see the spirit of the question. However, what I do is think of a different phrase/sentence for each password/situation and apply a certain algorithm on that. That way you're not limited to one good password.

---

### Post by benbenben on 2009-05-12
> **nobodysbusiness said:**
> If only there were some way to do something like this without trusting any specific website any more than you have to for the website to perform its function.

I don't think that this is possible as long as the website insists to be given the correct password - some machine must send that out and therefore be trusted to handle it.

> **nobodysbusiness said:**
> As an example, if you use the Dropbox online service to backup your files, and you encrypt the files before sending them over, then you don't have to trust the Dropbox people very much. After all, you're doing the encryption yourself...

But you wouldn't do the encryption/decryption on a computer you don't trust, would you? (I think that the settings of online backup and login from an internet cafe computer are too different for such a comparison.)

> **nobodysbusiness said:**
> Perhaps every website should have the ability to generate one-time codes as well as allowing a password-based login.

Banking sites do this for quite a while now (at least in Europe). If not requiring a one-time password for login, they at least require a one-time password for every transaction.

---

### Post by euler_fan on 2009-05-13
At least the following five realities need to be considered before worrying about a password generation scheme (which, thanks to any number of good random character generators is can be done without too much trouble if you're not too worried about the arcane world of psuedo-random number generators):

1) A well chosen password is probably the most secure part of any password system. So as long as it's easier to attack the browser or the site or the whatever than to try to brute force your password, awesome.

2) Most attackers don't care about getting your password, they care about getting someone's password. It's still easier to do this by social engineering targeted at the masses than guessing individual passwords.

3) Time spent guessing passwords is time not spent exploiting them. As such, there's more to be gained by making it take longer to guess any password than there is to be gained by trying to make it harder to guess a password.

4) Any decent password management software will include the ability to generate psuedo-random passwords and copy/paste them into whatever you need.

5) If you can memorize a ten digit phone number you can memorize ten random characters (which is ample to keep anyone from guessing it with a high degree of probability a long time, bonus points if you can post the correct formula for computing just how long at a given percentile of confidence)

---

