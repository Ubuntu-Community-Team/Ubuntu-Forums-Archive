---
title: "call for testing: hashicorp's vault"
date: 2017-03-07
forum: Ubuntu Development Version
---

### Post by elopio on 2017-03-07
Hello!

Here's one more snap ready for testing.

Vault is a tool to manage secrets in a secure way. So all the confinement properties that Ubuntu and snaps provide make it a perfect match. It's developed by Hashicorp, an amazing free software company that builds a cool set of tools for server infrastructure. So our interest with vault is to get it into the Ubuntu store with a flawless release process, in order to get all the other hashicorp tools following it.

Vault version 0.6.5 is in the stable channel, so you can get it with:

$ sudo snap install vault

version 0.7.0-beta1 is in the beta channel:

$ sudo snap install vault --beta

Here is the guide to get started testing:
[https://gist.github.com/elopio/e8481471a9b3964ccf5bf9f0c09605a9](https://gist.github.com/elopio/e8481471a9b3964ccf5bf9f0c09605a9)

You will notice that it only documents tests for the dev server. One very important thing to try before release is the server in a more real environment. And many more things to try can be found on the website docs:
[https://www.vaultproject.io/docs/index.html](https://www.vaultproject.io/docs/index.html)

It's very important to test the update process too. After installing from the stable channel:

$ sudo snap refresh vault --beta

As usual, please let me know how it goes. And if you have questions about vault or snaps, this is also a good moment to ask.

We will be following the pre-releases of 0.7, and I will be notifying you here when they are pushed to the Ubuntu store.

Thanks!
pura vida.

---

### Post by howefield on 2017-03-08
As per reply in mailing list.. tested on "Zesty" 7th March daily image. All tests completed as expected, with the exception of those smoke tests requiring AWS and github accounts which were not tested :(  

Update to beta version successful.

---

