# smime-nmh
Perl script handling gpgsm base smime in nmh

## install
```
    install gnupg
    install NKF.pm
```

sign shoul be linked to encode, put sign and encode into your bin.

## usage

In comp or repl,

```
   what now : edit mhn
   what now : edit sign
   what now : edit encode
```

## smime / key

You can get key as
```
   http://kb.mozillazine.org/Getting_an_SMIME_certificate
```

or create it by gpgsm 
for
  Enter the X.509 subject name: 
Answer like this
  C=JP, ST=Okinawa, L=Ginowan, O=Univerisy of the Ryukyus, OU=Faculty of Engineering, CN=kono@ie.u-ryukyu.ac.jp

```
  % gpgsm --generate-key -o email.pem
  % gpgsm --import emal.pem 
  % gpgsm --list-secret
```

if you want to use the key in Mail.app,

```
  % gpgsm  -o secret-gpg-key.p12   --export-secret-key-p12  0xkeyid
  % opn    secret-gpg-key.p12   
```
and trust it.

## comment

This is an easy example.

Basically, sign create two parts mime, which contains
```
   verifiable nested mime part with crlf
   signed.p7s
```
these can be verified by gpgsm --verify

Encode these verifiable two parts mime into single encrypted.p7m.

brew  gpgsm (GnuPG) 2.3.2 has corrupt --export-secret-key-p12 use gpgsm (GnuPG) 2.3.2-beta105

