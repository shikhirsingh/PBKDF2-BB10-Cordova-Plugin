# [PBKDF2](http://en.wikipedia.org/wiki/PBKDF2) - PBKDF2 for BB10 Cordova / Webworks

This Cordova/WebWorks plugin allows an app to hash a password using [PBKDF2](http://en.wikipedia.org/wiki/PBKDF2) for storage in a 
FAST manner. PBKDF2 is a [Key Derivation Function](http://en.wikipedia.org/wiki/Key_derivation_function) used for [securing passwords](https://crackstation.net/hashing-security.htm). 
The [OpenSSL](http://www.openssl.org/) Crypto library has been used to perform the hashing. 

The sample code for this application is Open Source under the [Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0.html).


**Author** 

* [Shikhir Singh](http://code.shikhir.com/)


**Release History**

* **V1.0.0** - Initial release

**Dependencies**

1. Minimal requirement for BlackBerry 10 Device Software is **10.0.9**
2. Minimal requirement for BlackBerry 10 Native SDK is **10.0.9**
3. Minimal requirement for BlackBerry 10 Webworks is **2.0**


**How to install this extension**

In command prompt while in your Cordova/WebWorks project directory, type: cordova plugin add <path to the /plugin/ directory>

**How to Build SMS for BB10 Cordova**

Assumption: You have installed the BlackBerry Native SDK 2.0+, and BlackBerry Webworks 2.0+

1. Simply import the NDK_project directory into a workspace in your NDK. Build the project. 
2. After building the NDK Project, copy the contents of the NDK_project directory into plugin/src/blackberry10/native - Here is the command: cp -R NDK_project/ plugin/src/blackberry10/native 
3. Go to the SMSPlugin-DemoApp directory, then add the plugin using the following command: cordova plugin add ../plugin/
4. Now you can build the project using : cordova build --release --keystorepass YOUR_PASSWORD_GOES_HERE -buildId 1 

**Usage**

```
var passwdParam = {
	"password": "MyPassword",  
	"salt": "MySalt", // 
	"iterations": 50000, 
	"keyLength": "32" //  is bytes, not bits!
};
						
var hashedValue=community.PasswordCrypto.pbkdf2_Sync(passwdParam); 
```
**Iterations**
Iterations as well as the keylength determine the speed of the algorithm. You want the algorithm to be slow to be secure, but not slow
enough to irratate the user. A minimum iterations count of around 30,000 at a key length of 32 bytes is recommended. 

 
**Sample App**

A sample app has been included only so that you may compare the speed of the algorithm with a JavaScript implementation vs the C++ implementation. JavaScript implementation of the algorithm is [here](http://anandam.name/pbkdf2/) under BSD license. 

If you don't want to build this sample application yourself we've included a pre-built and signed BAR file. 
You can find it in the folder /build/ folder. 


**Known Issues**

None! 


## Contributing Changes

Please see the [README](https://github.com/blackberry/Cascades-Community-Samples/blob/master/README.md) of the Cascades-Community-Samples repository for instructions on how to add new Samples or make modifications to existing Samples.



## Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING 
BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE 
AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR 
ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR 
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR 
OTHER DEALINGS IN THE SOFTWARE.