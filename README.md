## This repository describes accessibility issue with electron with iframes embedded inside webview

# Please find the details on the issue below
Link to issue: https://github.com/electron/electron/issues/24589

* **Electron Version(s)**
  * `1.3.1`, `1.8.4`, `8.4.0`, `9.1.0` & `10.0.0-beta.12`
* **Operating System:**
  * MacOS
* **Last Known Working Electron version:**
  * NA

### Expected Behavior
<img width="551" alt="Screen Shot 2020-07-16 at 4 21 27 PM" src="https://user-images.githubusercontent.com/9450414/87662802-69068e00-c780-11ea-8aea-426c189b3a9a.png">
I have an app which has 3 levels, level1 incudes a webview with page source level2.html; inside level2 an `<iframe>` element is embedded with source set to level3.html. Each page has button & input field.

The expected behavior would be while tabbing the screen readers should be able to focus & read through all three buttons & input fields.

### Actual Behavior
Screen readers are reaching till the buttons & input fields of level 2 & ignoring level3. But if I relace `<webview>` with `<iframe>` everything seems to work fine.
[Please check out the video for more details on the issue](https://www.loom.com/share/318395aa07f54592bd047f6afa4b300a)

**Check the below image showing the accessibility tree not being generated properly incase of webview**:
<img width="977" alt="Screen Shot 2020-07-16 at 4 36 20 PM" src="https://user-images.githubusercontent.com/9450414/87664530-0498fe00-c783-11ea-8b27-cfff4ad1eedd.png">

### To Reproduce
- Clone this repository
   $ git clone https://github.com/sarthak-saxena/electron-webview-issue
   $ cd electron-quick-start
   $ npm install
   $ npm start || electron .

- Turn on the screen reader
- Tab across button & input fields
- You will notice that the screen reader focus is not moving to level3 hence is not able to read the corresponding elements


### Additional Information
This issue has been reported earlier & is a possible duplicate of https://github.com/electron/electron/issues/12478 but it contains more information on reproducing the bug  for electron version `8.4.0`
