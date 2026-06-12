---
title: "Complete Images?"
date: 2006-09-28
forum: Server Platforms
---

### Post by JD_2020 on 2006-09-28
Hi --

Been putzing around with Ubuntu and am really rather sick of trying to configure my web server. Lots of problems, I tried doing it all piece-by-piece, MySQL shat itself, so I tried getting LAMPP... Then I needed a perl module, CPAN didn't recognize the perl LAMPP installed... Problem after problem.

Are there any images that just are completely setup? Some image that a script runs, you do a simple configuration and it automatically installs and configures linux for you and you're ready to just use it?

Thanks,
-JD

---

### Post by bluefrog on 2006-09-28
my advice... 
install "normal" ubuntu.
open synaptic and enable universe / multiverse repository.
reload (in synaptic)
install apache2, php (4 or 5), mysql (4 or 5).

you're done.

As it seems you are not well prepared to do it by hand, you should use the perl packages available in synaptic and not fiddle with them manually from the CPAN prompt.

James

---

