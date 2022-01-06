# MailCore

A package wrapping MailCore2 macOS universal framework.
See [original MailCore2 repository](https://github.com/MailCore/mailcore2).

# Why ?

Because MailCore2 framework available through SPM hasn't been build for arm64 architectures.

# How ?

MailCore2 macOS universal framework is wrapped inside an XCFramework, and this in turn is wrapped here.
MailCore2 framework depends on two libraries :

- [libctemplate](https://github.com/dinhviethoa/ctemplate) : at revision b50f83f26ce3658889db1ae41b6a2d5874a3a10f
- [libetpan](https://github.com/dinhviethoa/libetpan.git) : at revision 5164ba2ebd3c7cbc7a9230aad32bdf8e24e207de

Those two libraries have been built as universal libraries, and MailCore2 as well linking with the two.
Finally, the XCFramework was created using `xcodebuild`:

```
> $ xcodebuild -create-xcframework -framework MailCore.framework -output MailCore.xcframework 
```

