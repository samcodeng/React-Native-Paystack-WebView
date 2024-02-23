# React Native Paystack WebView

This is an updated version to the original fork

The package allows you accept payment using paystack, install, add keys and use. No stress :) 

### [](https://github.com/samcodeng/Samcode-React-Native-Paystack-WebView#installation)Installation

Add React-Native-Paystack-WebView to your project by running;

`npm install samcode-react-native-paystack-webview`

or

`yarn add samcode-react-native-paystack-webview`

### **One more thing**

To frontload the installation work, let's also install and configure dependencies used by this project, being **react-native-webview** 

run

`yarn add react-native-webview`

for iOS: `cd iOS && pod install && cd ..`

for expo applications run;

`expo install react-native-webview`

and that's it, you're all good to go!

<img width="306" alt="Screenshot of library in action" src="https://user-images.githubusercontent.com/41248079/126550307-5f12c6d8-81af-4f26-951b-5d6514304022.png">

### [](https://github.com/samcodeng/Samcode-React-Native-Paystack-WebView#usage)Usage 1

```javascript
import React from 'react';
import  { Paystack }  from 'react-native-paystack-webview';
import { View } from 'react-native';

function Pay() {
  return (
    <View style={{ flex: 1 }}>
      <Paystack  
        paystackKey="your-public-key-here"
        amount={'25000.00'}
        billingEmail="paystackwebview@something.com"
        activityIndicatorColor="green"
        onCancel={(e) => {
          // handle response here
        }}
        onSuccess={(res) => {
          // handle response here
        }}
        autoStart={true}
      />
    </View>
  );
}
```

## Usage 2 - Using Refs

Make use of a `ref` to start transaction. See example below;

```javascript
import React, { useRef } from 'react';
import  { Paystack , paystackProps}  from 'react-native-paystack-webview';
import { View, TouchableOpacity,Text } from 'react-native';

function Pay(){
  const paystackWebViewRef = useRef<paystackProps.PayStackRef>(); 

  return (
    <View style={{flex: 1}}>
      <Paystack
        paystackKey="your-public-key-here"
        billingEmail="paystackwebview@something.com"
        amount={'25000.00'}
        onCancel={(e) => {
          // handle response here
        }}
        onSuccess={(res) => {
          // handle response here
        }}
        ref={paystackWebViewRef}
      />

        <TouchableOpacity onPress={()=> paystackWebViewRef.current.startTransaction()}>
          <Text>Pay Now</Text>
        </TouchableOpacity>
      </View>
  );
}
```

## API's

#### [](https://github.com/just1and0/object-to-array-convert#all-object-to-array-convert-props)all React-Native-Paystack-WebView API

| Name                                 |                                                                                           use/description                                                                                           |                                                      extra |
| :----------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | ---------------------------------------------------------: |
| `paystackKey`                        |                                                                   Public or Private paystack key(visit paystack.com to get yours)                                                                   |                                                     `nill` |
| `amount`                             |                                                                                          Amount to be paid                                                                                          |                                                     `nill` |
| `activityIndicatorColor`             |                                                                                           color of loader                                                                                           |                                           default: `green` |
| `billingEmail(required by paystack)` |                                                                                            Billers email                                                                                            |                                            default: `nill` |
| `billingMobile`                      |                                                                                           Billers mobile                                                                                            |                                            default: `nill` |
| `billingName`                        |                                                                                            Billers Name                                                                                             |                                            default: `nill` |
| `channels`                           | Specify payment options available to users. Available channel options are: ["card", "bank", "ussd", "qr", "mobile_money"]. Here's an example of usage: `channels={["card","ussd"]}`                 |                                         default: `["card"]`|
| `onCancel`                           |               callback function if user cancels or payment transaction could not be verified. In a case of not being verified, transactionRef number is also returned in the callback               |                                            default: `nill` |
| `onSuccess`                          |                                    callback function if transaction was successful and verified (it will also return the transactionRef number in the callback )                                    |                                            default: `nill` |
| `autoStart`                          |                                                                               Auto start payment once page is opened                                                                                |                                           default: `false` |
| `refNumber`                          |                                                                         Reference number, if you have already generated one                                                                         | default: `''+Math.floor((Math.random() * 1000000000) + 1)` |
| `handleWebViewMessage`               |                                                                          Will be called when a WebView receives a message                                                                           |                                            default: `true` |



## [](https://github.com/samcodeng/Samcode-React-Native-Paystack-WebView#licensing)Licensing

This project is licensed under MIT license.

## Related Projects
=
### Video Tutorial

- [Accepting Payment With Paystack In React Native](https://www.youtube.com/watch?v=M-V4Q9zk9DE&t=19s) by [just1and0](https://twitter.com/just1and0)


<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!


# Roadmap
we have a lot to get done before we hit stable, here's a list;
- Make the reference usage more user friendly
- Since you want it to conform to InlineJS, let the variable names also match
- Let the parameter types also conform to InlineJS parameter types
- Paystack is a word, hence when used as a package name/class name, let it use PascalCase (Paystack) and when used as a variable, camelCase (paystack)
