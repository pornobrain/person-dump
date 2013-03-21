Load the dump:
```
% tar xvf person-dump.tar.xz
% mongorestore -d pornobrain pornobrain
```

Some queries:
```
% mongo iafd
> db.Person.findOne({name: /sasha.*grey/i}, {birthday: 1, name: 1, aka: 1})
{
  "_id" : {
		"id" : "SashaGrey",
		"gender" : "Female"
	},
	"name" : "Sasha Grey",
	"aka" : [
		"Sasha Gray",
		"Sascha Grey"
	],
	"birthday" : ISODate("1988-03-14T00:00:00Z")
}
> db.Person.findOne({name: /sasha.*grey/i}, {movies: 1}).movies[0]
{
	"movie" : DBRef("Movie", {
	"title" : "12+nasty+girls+masturbating+8",
	"year" : 2006,
	"slug" : "12-nasty-girls-masturbating-8"
}),
	"notes" : [
		"MastOnly"
	]
}
> db.Person.findOne({name: /sasha.*grey/i}, {movies: 1}).movies[1]
{
	"movie" : DBRef("Movie", {
	"title" : "18yearsold%2ecom+2",
	"year" : 2007,
	"slug" : "18yearsold%2ecom-2"
}),
	"notes" : [
		"Anal",
		"Facial",
		"Swallow",
		"A2M"
	]
}
```

Source code used to extract this data: [pornobrain/iafd-recommend](http://github.com/pornobrain/iafd-recommend)
