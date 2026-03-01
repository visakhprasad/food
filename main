import React, { useState } from 'react';
import { Utensils, MapPin, Receipt, Star, ImagePlus, Plus, X, User, Camera } from 'lucide-react';

export default function App() {
  const [currentUser, setCurrentUser] = useState('');
  const [isAdding, setIsAdding] = useState(false);
  
  // Mock initial data to show how it looks
  const [posts, setPosts] = useState([
    {
      id: 1,
      author: 'You',
      restaurant: 'Spicy Symphony',
      location: 'Downtown',
      dishes: 'Garlic Butter Prawns, Truffle Risotto',
      cost: 45,
      rating: 5,
      review: 'Absolutely mind-blowing. The risotto was perfectly cooked and the prawns had the perfect kick to them. A bit pricey but worth every penny for a nice dinner.',
      image: 'https://images.unsplash.com/photo-1633337474564-1d9478dd4efb?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
      date: 'Just now'
    },
    {
      id: 2,
      author: 'Alex (Friend)',
      restaurant: 'Burger Joint',
      location: 'Westside',
      dishes: 'Double Smashburger, Truffle Fries',
      cost: 18,
      rating: 4,
      review: 'Great late-night spot. The smashburger crust was incredible. Fries were a little salty for my taste, but overall a solid 4/5.',
      image: 'https://images.unsplash.com/photo-1568901346375-23c9450c58cd?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
      date: '2 days ago'
    }
  ]);

  // Form State
  const [formData, setFormData] = useState({
    restaurant: '', location: '', dishes: '', cost: '', rating: 5, review: '', image: ''
  });

  const handleImageUpload = (e) => {
    const file = e.target.files[0];
    if (file) {
      const imageUrl = URL.createObjectURL(file);
      setFormData({ ...formData, image: imageUrl });
    }
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    const newPost = {
      ...formData,
      id: Date.now(),
      author: currentUser,
      date: 'Just now'
    };
    setPosts([newPost, ...posts]);
    setIsAdding(false);
    setFormData({ restaurant: '', location: '', dishes: '', cost: '', rating: 5, review: '', image: '' });
  };

  // Login Screen (Mock)
  if (!currentUser) {
    return (
      <div className="min-h-screen bg-orange-50 flex items-center justify-center p-4">
        <div className="bg-white p-8 rounded-2xl shadow-xl max-w-md w-full text-center">
          <div className="bg-orange-100 w-20 h-20 rounded-full flex items-center justify-center mx-auto mb-6">
            <Utensils className="text-orange-600 w-10 h-10" />
          </div>
          <h1 className="text-3xl font-bold text-gray-800 mb-2">BiteClub</h1>
          <p className="text-gray-500 mb-8">Your private circle for food reviews.</p>
          
          <div className="space-y-4">
            <input 
              type="text" 
              placeholder="Enter your name to join..." 
              className="w-full p-4 border border-gray-200 rounded-xl focus:ring-2 focus:ring-orange-500 focus:outline-none"
              onKeyDown={(e) => {
                if (e.key === 'Enter' && e.target.value) setCurrentUser(e.target.value);
              }}
              id="nameInput"
            />
            <button 
              onClick={() => {
                const name = document.getElementById('nameInput').value;
                if (name) setCurrentUser(name);
              }}
              className="w-full bg-orange-600 text-white font-bold py-4 rounded-xl hover:bg-orange-700 transition"
            >
              Enter the Club
            </button>
          </div>
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-gray-50 pb-20">
      {/* Header */}
      <header className="bg-white shadow-sm sticky top-0 z-10">
        <div className="max-w-2xl mx-auto px-4 py-4 flex justify-between items-center">
          <div className="flex items-center gap-2">
            <Utensils className="text-orange-600 w-6 h-6" />
            <h1 className="text-xl font-bold text-gray-800">BiteClub</h1>
          </div>
          <div className="flex items-center gap-2 text-sm font-medium text-gray-600 bg-gray-100 px-3 py-1.5 rounded-full">
            <User className="w-4 h-4" />
            {currentUser}
          </div>
        </div>
      </header>

      {/* Main Feed */}
      <main className="max-w-2xl mx-auto p-4 space-y-6 mt-4">
        {posts.map(post => (
          <div key={post.id} className="bg-white rounded-2xl shadow-sm overflow-hidden border border-gray-100">
            {post.image && (
              <div className="w-full h-64 overflow-hidden bg-gray-100">
                <img src={post.image} alt={post.restaurant} className="w-full h-full object-cover" />
              </div>
            )}
            <div className="p-5">
              <div className="flex justify-between items-start mb-3">
                <div>
                  <h2 className="text-2xl font-bold text-gray-800">{post.restaurant}</h2>
                  <div className="flex items-center text-gray-500 text-sm mt-1 gap-4">
                    <span className="flex items-center gap-1"><MapPin className="w-4 h-4" /> {post.location}</span>
                    <span className="flex items-center gap-1"><Receipt className="w-4 h-4" /> ${post.cost}</span>
                  </div>
                </div>
                <div className="flex bg-orange-50 px-2 py-1 rounded-lg">
                  {[...Array(5)].map((_, i) => (
                    <Star key={i} className={`w-4 h-4 ${i < post.rating ? 'text-orange-500 fill-orange-500' : 'text-gray-300'}`} />
                  ))}
                </div>
              </div>

              <div className="mb-4">
                <span className="text-xs font-bold uppercase tracking-wider text-orange-600 mb-1 block">What we ate</span>
                <p className="text-gray-700 font-medium">{post.dishes}</p>
              </div>

              <div className="bg-gray-50 p-4 rounded-xl relative">
                <p className="text-gray-600 italic text-sm leading-relaxed">"{post.review}"</p>
              </div>

              <div className="mt-4 flex items-center justify-between text-xs text-gray-400">
                <span>Posted by <strong className="text-gray-700">{post.author}</strong></span>
                <span>{post.date}</span>
              </div>
            </div>
          </div>
        ))}
      </main>

      {/* Floating Add Button */}
      <button 
        onClick={() => setIsAdding(true)}
        className="fixed bottom-6 right-6 bg-orange-600 text-white p-4 rounded-full shadow-lg hover:bg-orange-700 transition transform hover:scale-105 z-20"
      >
        <Plus className="w-6 h-6" />
      </button>

      {/* Add Entry Modal */}
      {isAdding && (
        <div className="fixed inset-0 bg-black/50 z-50 flex items-end sm:items-center justify-center sm:p-4">
          <div className="bg-white w-full sm:max-w-lg rounded-t-2xl sm:rounded-2xl max-h-[90vh] overflow-y-auto">
            <div className="sticky top-0 bg-white border-b border-gray-100 p-4 flex justify-between items-center z-10">
              <h2 className="text-lg font-bold">New Food Review</h2>
              <button onClick={() => setIsAdding(false)} className="p-2 hover:bg-gray-100 rounded-full">
                <X className="w-5 h-5" />
              </button>
            </div>
            
            <form onSubmit={handleSubmit} className="p-5 space-y-5">
              
              {/* Image Upload Area */}
              <div className="relative">
                {formData.image ? (
                  <div className="relative h-48 rounded-xl overflow-hidden group">
                    <img src={formData.image} alt="Preview" className="w-full h-full object-cover" />
                    <button 
                      type="button" 
                      onClick={() => setFormData({...formData, image: ''})}
                      className="absolute top-2 right-2 bg-black/50 text-white p-1.5 rounded-full"
                    >
                      <X className="w-4 h-4" />
                    </button>
                  </div>
                ) : (
                  <label className="flex flex-col items-center justify-center w-full h-32 border-2 border-dashed border-gray-300 rounded-xl cursor-pointer hover:bg-gray-50 transition">
                    <div className="flex flex-col items-center justify-center pt-5 pb-6 text-gray-500">
                      <Camera className="w-8 h-8 mb-2 text-gray-400" />
                      <p className="text-sm font-medium">Click to upload food photo</p>
                    </div>
                    <input type="file" className="hidden" accept="image/*" onChange={handleImageUpload} />
                  </label>
                )}
              </div>

              <div className="grid grid-cols-2 gap-4">
                <div className="col-span-2">
                  <label className="text-sm font-bold text-gray-700 block mb-1">Restaurant Name</label>
                  <input required type="text" className="w-full p-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-orange-500 outline-none" placeholder="e.g. Joe's Pizza" 
                    value={formData.restaurant} onChange={e => setFormData({...formData, restaurant: e.target.value})} />
                </div>
                
                <div>
                  <label className="text-sm font-bold text-gray-700 block mb-1">Location / Area</label>
                  <input required type="text" className="w-full p-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-orange-500 outline-none" placeholder="e.g. Brooklyn" 
                    value={formData.location} onChange={e => setFormData({...formData, location: e.target.value})} />
                </div>

                <div>
                  <label className="text-sm font-bold text-gray-700 block mb-1">Total Bill ($)</label>
                  <input required type="number" className="w-full p-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-orange-500 outline-none" placeholder="0.00" 
                    value={formData.cost} onChange={e => setFormData({...formData, cost: e.target.value})} />
                </div>
              </div>

              <div>
                <label className="text-sm font-bold text-gray-700 block mb-1">What did you eat?</label>
                <input required type="text" className="w-full p-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-orange-500 outline-none" placeholder="e.g. Pepperoni slice, Garlic knots" 
                  value={formData.dishes} onChange={e => setFormData({...formData, dishes: e.target.value})} />
              </div>

              <div>
                <label className="text-sm font-bold text-gray-700 block mb-2">Your Rating</label>
                <div className="flex gap-2">
                  {[1, 2, 3, 4, 5].map(star => (
                    <button 
                      key={star} type="button" 
                      onClick={() => setFormData({...formData, rating: star})}
                      className="p-1 focus:outline-none transform hover:scale-110 transition"
                    >
                      <Star className={`w-8 h-8 ${formData.rating >= star ? 'text-orange-500 fill-orange-500' : 'text-gray-300 fill-gray-100'}`} />
                    </button>
                  ))}
                </div>
              </div>

              <div>
                <label className="text-sm font-bold text-gray-700 block mb-1">Your Review</label>
                <textarea required rows="3" className="w-full p-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-orange-500 outline-none resize-none" placeholder="What did you think of the food, vibe, and service?" 
                  value={formData.review} onChange={e => setFormData({...formData, review: e.target.value})}></textarea>
              </div>

              <button type="submit" className="w-full bg-orange-600 text-white font-bold py-4 rounded-xl hover:bg-orange-700 transition">
                Post Review
              </button>
            </form>
          </div>
        </div>
      )}
    </div>
  );
}
