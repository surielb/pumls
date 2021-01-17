# Nominations

![diagram](http://www.plantuml.com/plantuml/png/5SZB3O0W303GLNG1UdSRm4QQz4FwYUiRt_6Tf9Fhnd8-LkQE2y3xsnxALQC2VPecQhPf0b5Eo0Ds2GT89mKr8Ur9fj7-_W00)

## Elements

### `NominationItem`

The `NominationItem` is the base element. the idea is it can be re-used across different teams and organizations o allow later on a way to compare
nominations and awards across users, teams and organizations.

At the base is a `NominationItem` it has a Title, a description, an image and a list of tags to help index for later search.
A `NominationItem` is localizable to allow the same item to appear in multiple languages.

> Note: although a `NominationItem` is "global" it can be restricted to a specific organization to allow custom nominations in specific ogs and teams

### `Nominations`

`Nominations` are simpley a collection of [Nomination Items](#nominationitem) that has been curated in advance.
this is the blue-print of a new challenge, much like a trivia challenge has been pre-curated with questions and a manager can choose which/how many `NominationItem`s
they wish to enable from the collection for a challenge

### `NominationsChallengeItem`

a `NominationsChallengeItem` is an active challenge that was created from a [Nominations](#nominations) collection.
It creates a [`NominationHolder`](#nominationholder) for each [`NominationItem`](#nominationitem) to store the [votes](#nominationvote) given by team members throughout the challenge 

### `NominationHolder`

A nomination holder holds the votes made by team members for each item. it is the progress of the voting in the challenge

### `NominationVote`

Each team member gets to "vote" who they wish to "award" a nomination to. the list of available entrees would be the other team members.
and the end of the challenge a user with the most votes would be "awarded" the nomination


### `NominationAward`

When the challenge has completed, "awards" are given to the team members based on the votes they recieved.
In addition to their award being presented in the challenge's result it will be added to the users profile.
An award is added to a user's `NominationAward` for that `NominationItem`

### `NominationAward`

To keep track of awards user's have received, when a user has been voted 1st for a `NominationItem` in a chellenge, it will be added to a special `NomintaionAward` element.
This will allow us to add a special badge to their profile, or just add a page on their profile with "Awards" containing a list of all the "Awards" they have won.

a `NominationAward` has a list of references to the `NominationHolder` that holds the 'votes' that nominated them.

This means that a user can win the same "Nomination" multiple time in different challenges on different dates. which will also allow us to add fun things like:

"Voted 'Code-Breaker' 5 weeks in a row" etc.
