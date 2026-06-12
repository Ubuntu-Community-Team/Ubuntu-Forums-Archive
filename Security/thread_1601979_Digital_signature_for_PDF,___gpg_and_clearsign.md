---
title: "Digital signature for PDF,   gpg and clearsign"
date: 2010-10-20
forum: Security
---

### Post by keirvt on 2010-10-20
I wrote some code to digitally sign a PDF document without having to buy certificated from Adobe.
It uses a trick that any line in a PDF beginning with a percent character is a comment.

The gpg command has a "clearsign" flag which generates the digital signature in a nice ascii form that can be attached to the PDF.

So you sign the document but then edit the header and footer to add the percent character so pdf readers don't gag.

The verification web page  strips the percent sign and then verifies the document as usual.

Everything works great except......

It seems that there is a limit on the size of the input file when using the clearsign flag. that produces the error
"gpg: input line longer than 19995 characters"

Without clearsign there is apparently no limit but then everything is in binary and a signed PDF is corrupted by the signature.

Is there a way to increase the size of an input file when using the clearsign flag?

---

