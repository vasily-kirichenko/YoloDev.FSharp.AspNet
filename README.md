FSharpSupport
=============
![build status](http://img.shields.io/appveyor/ci/Alxandr/fsharpsupport-117.svg?style=flat)
![repo size](https://reposs.herokuapp.com/?path=YoloDev/FSharpSupport&style=flat)

FSharp Support for K

Usage
===
#### Step 1.
Add the yolodev myget feed to your `NuGet.Config` file. This file should be in your Solution folder. If it does not exist yet, you must create one. Proper casing of the filename is important! 

Sample:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <packageSources>
    <add key="YoloDev" value="https://www.myget.org/F/yolodev/api/v2" />
    <add key="AspNetVNext" value="https://www.myget.org/F/aspnetvnext/api/v2" />
    <add key="NuGet.org" value="https://nuget.org/api/v2/" />
  </packageSources>
</configuration>
```

#### Step 2.
Create a new `ASP.NET vNext Empty Web Application` or `ASP.NET vNext Desktop Application` project in Visual Studio 2014. The new project system uses a `project.json` file to list all the dependencies. This file resides in the root folder of the project. Add the FSharpSupport library as a dependency. Because we're going to use an other language than C# we have to add a "language" key to the project.json file. You also need to add sources, since the default one just goes looking for *.cs. This is also quite important in F#, since file order matters. So be sure you list the sources in the right order. 

Sample:

```js
{
    "dependencies": {
        "FSharpSupport": "0.1-*"
    },
    "code": [ "file1.fs", "file2.fs" ],
    "language": {
        "name": "F#",
        "assembly": "FSharpSupport",
        "projectReferenceProviderType": "FSharpSupport.FSharpProjectReferenceProvider"
    },
    "frameworks": {
        "net45": { }
    }
}
```

#### Step 3.
Code whatever you want in F#! Have fun!

#### Step 4.
Down to bussiness again. As there is no tooling support for F# together with vNext yet there is some manual labor required. Open up a `Developer Command Prompt`, this is a command prompt with a few required paths of tools pre-loaded. A link to this tool resides in the `Visual Studio Tools` folder in your start screen. The shortcut is also found in `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\Shortcuts`.

Navigate to your project folder in the command prompt, to the folder where the `project.json` is. Enter `k run` or `k web`. Now watch the magic or go fix your bugs!

#### Step 5.
Profit! Yes, it's that simple.
