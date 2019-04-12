# nugetprojectjson
Scripting to convert projects with packages.config to a project with project.json nuget depedencies.
Will recusively walk all subfolders of the folder from which it was called.

Please note that it might also convert packages.config that is in your .nuget.
besides converting packages.config to project.json it also changes the csproj files:
* Removes all hint paths to nuget dependency assemblies.
* removes packages.config from csproj
* Removes EnsureNugetPackageBuildImports
* Add project.json file

Add a couple of properties that have been found by users to make sure that for example Nunit assemblies are copied to the output folder.
* add targetFrameworkProfile property
* Does NOT add CopyNuGetImplementations = true property, this should only be set for Test projects (NUnit,xUnit ,MSTest) and Executables.
  See https://github.com/wgtmpeters/nugetprojectjson/issues/1
* add PlatformTarget AnyCpu

* replace toolsversion with "14.0"

Switch -redo will regenerate the project.json files based on the packages_old.config that have been renamed by a earlier run of the script.

Switch -f will change the target framework. E.g. `-f net461`