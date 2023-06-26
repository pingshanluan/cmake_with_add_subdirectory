To include headers in CMake targets, use the command 

    target_include_directories(...)

Depending on the purpose of the included directories, you will need to define the scope specifier – either 
        PUBLIC
        PRIVATE 
        INTERFACE

PUBLIC and PRIVATE scopes mean exactly what you would expect in an inheritance context: 
    PUBLIC will make the directories available in the current target and the dependent targets 
    PRIVATE will only make the directories available for the current target, not the dependents.
    The INTERFACE keyword is the most difficult to understand, as its uses are rarely needed for basic projects: it makes the directories available for dependent targets but not the target declaring the directories!

As a general note: always use PRIVATE by default, this will keep scope small and simplify your CMake dependency graph. If you absolutely need to export header directories with the target, use PUBLIC.

If you still don’t understand the scopes, I’d recommend the CMake documentation and this article on CMake Public vs Private vs Interface by Lei Mao, he makes some good analogies there!